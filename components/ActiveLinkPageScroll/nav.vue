<script setup lang="ts">
interface SctionMaps {
  sectionId: any;
  sectionColor: any;
  top: number;
  bottom: number;
}
let oldViewPortVertical: number;

const activeClass = ref();
const sctionMaps = ref<SctionMaps[]>([]);
const navHegiht = ref(0);

const moveLikedBySectionId = (sectionId: string) => {
  const find = sctionMaps.value.filter((v) => v.sectionId === sectionId);
  // console.log(find[0].top);
  scrollTo({
    top: find[0].top - navHegiht.value,
    behavior: "auto",
  });
};

const obsLink = () => {
  let catchC = "";
  const catchScroll = scrollY + navHegiht.value;

  for (let i = 0; i < sctionMaps.value.length; i++) {
    if (
      sctionMaps.value[i].top <= catchScroll &&
      catchScroll < sctionMaps.value[i].bottom
    ) {
      catchC = sctionMaps.value[i].sectionId;
      break;
    }
  }
  activeClass.value = catchC;
};

const resizeVertical = () => {
  // 수직 이벤트에만
  // if (oldViewPortVertical === document.documentElement.clientHeight) return;
  oldViewPortVertical = document.documentElement.clientHeight;

  sctionMaps.value.length = 0;
  navHegiht.value =
    document.querySelector("header")?.getBoundingClientRect().bottom || 0;

  const sections = document.querySelectorAll("section[data-section-id]");
  sections.forEach((el) => {
    // console.log(el.dataset.sectionId, el.dataset.sectionColor);

    const { sectionId, sectionColor } = (el as HTMLElement).dataset;
    sctionMaps.value.push({
      sectionId,
      sectionColor,
      top: el.getBoundingClientRect().top,
      bottom: el.getBoundingClientRect().bottom,
    });
  });

  setTimeout(() => {
    scrollTo({
      top: 0,
      left: 0,
      behavior: "instant",
    });
  }, 0);
};

onMounted(() => {
  resizeVertical();
  oldViewPortVertical = document.documentElement.clientHeight;

  window.addEventListener("scroll", obsLink);
  window.addEventListener("resize", resizeVertical);
  obsLink();
});
onUnmounted(() => {
  window.removeEventListener("scroll", obsLink);
  window.removeEventListener("resize", resizeVertical);
});
</script>

<template>
  <header>
    <div class="header-wrap max-w-dialogue">
      <a href="#" class="logo">김주찬</a>
      <nav>
        <div
          @click="moveLikedBySectionId(item.sectionId)"
          v-for="item in sctionMaps"
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
  @apply sticky left-0 top-0 w-full flex justify-center overflow-hidden bg-[#333];

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
