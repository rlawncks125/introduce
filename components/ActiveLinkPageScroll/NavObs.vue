<script setup lang="ts">
interface SctionMaps {
  sectionId: any;
  sectionColor: any;
  el: Element;
}

const activeClass = ref();
const navHegiht = ref(0);
const sectionMaps = ref<SctionMaps[]>([]);
const visiblesSections = ref<boolean[]>([]);
let observer: IntersectionObserver;

function ObserverCallback(entries: IntersectionObserverEntry[]) {
  entries.forEach((entry) => {
    const index = sectionMaps.value.findIndex(
      (v) => v.sectionId === (entry.target as HTMLElement).dataset.sectionId
    );
    visiblesSections.value[index] = entry.isIntersecting;
  });
  const visibles = visiblesSections.value.indexOf(true);
  activeClass.value = sectionMaps.value[visibles].sectionId;
}

function moveLikedBySectionId(sectionId: any) {
  const section = sectionMaps.value.find((v) => v.sectionId === sectionId);

  const y = section?.el.getBoundingClientRect().top! + window.scrollY;
  const top = y - (navHegiht.value - 2);
  window.scroll({
    top,
    left: 0,
    behavior: "auto",
  });
}

function resizeInit() {
  observer.disconnect();

  sectionMaps.value.forEach((el) => {
    observer.observe(el.el);
  });
}

onMounted(() => {
  navHegiht.value =
    document.querySelector("header")?.getBoundingClientRect().bottom || 0;

  const options = {
    root: window.document,
    rootMargin: `-${navHegiht.value}px 0px 0px 0px`,
    threshold: [0, 0.98],
  } as IntersectionObserverInit;

  observer = new IntersectionObserver(ObserverCallback, options);

  const sections = document.querySelectorAll("section[data-section-id]");

  sections.forEach((el) => {
    // console.log(el.dataset.sectionId, el.dataset.sectionColor);
    observer.observe(el);

    const { sectionId, sectionColor } = (el as HTMLElement).dataset;
    sectionMaps.value.push({
      sectionId,
      sectionColor,
      el,
    });
  });

  visiblesSections.value = sectionMaps.value.map(() => false);

  window.addEventListener("resize", resizeInit);
});
onUnmounted(() => {
  window.removeEventListener("resize", resizeInit);
});
</script>

<template>
  <header>
    <div class="header-wrap max-w-dialogue">
      <a href="#" class="logo">김주찬</a>
      <nav>
        <div
          @click="moveLikedBySectionId(item.sectionId)"
          v-for="item in sectionMaps"
          class="linked cursor-pointer"
          :class="activeClass == item.sectionId ? 'active' : ''"
          :style="`--clr: ${item.sectionColor}`"
        >
          {{ item.sectionId }}
        </div>
      </nav>
    </div>
  </header>
</template>

<style lang="scss">
header {
  @apply z-[10000] sticky left-0 top-0 w-full flex justify-center overflow-hidden bg-[#333];

  & .header-wrap {
    @apply px-[25px] flex-row-reverse;
    @apply w-full sm:px-[50px] pt-[10px] flex sm:flex-row justify-between items-center;
  }

  & .logo {
    @apply relative top-[-7px] text-[2em] text-[#fff] font-[700];
  }
}

.header-wrap nav {
  @apply flex gap-[10px];

  .linked {
    @apply hidden;
    @apply sm:block relative text-[#fff] font-[600] py-[12px] px-[20px] hover:text-pink-300;

    &.active {
      @apply block text-[#333] rounded-l-[10px] rounded-r-[10px];

      background: var(--clr);
    }
    &.active::before {
      content: "";
      @apply w-[20px] h-[20px] absolute left-[-20px] bottom-0 bg-transparent;
      border-bottom-right-radius: 20px;
      box-shadow: 10px 5px 0 5px var(--clr);
    }
    &.active::after {
      content: "";
      @apply w-[20px] h-[20px] absolute right-[-20px] bottom-0 bg-transparent;

      border-bottom-left-radius: 20px;
      box-shadow: -10px 5px 0 5px var(--clr);
    }
  }
}
</style>
