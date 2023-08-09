<script setup lang="ts">
interface SctionMaps {
  sectionId: any;
  sectionColor: any;
  top: number;
}

const activeClass = ref();
const sctionMaps = ref<SctionMaps[]>([]);
const navHegiht = ref(0);

const moveLikedBySectionId = (sectionId: string) => {
  const find = sctionMaps.value.filter((v) => v.sectionId === sectionId);
  // console.log(find[0].top);
  scrollTo({
    top: find[0].top - navHegiht.value,
    behavior: "smooth",
  });
};

const obsLink = () => {
  let catchC = "";
  const catchScroll = scrollY + navHegiht.value;
  sctionMaps.value.reduce((a, b) => {
    if (a.top <= catchScroll && catchScroll < b.top) {
      catchC = a.sectionId;
    }
    return b;
  }, sctionMaps.value[0]);
  activeClass.value =
    catchC || sctionMaps.value[sctionMaps.value.length - 1].sectionId;
  // console.log(catchScroll, catchC, scrollY);
};

onMounted(() => {
  navHegiht.value =
    document.querySelector("header")?.getBoundingClientRect().bottom || 0;

  const sections = document.querySelectorAll("section");
  sections.forEach((el) => {
    // console.log(el.dataset.sectionId, el.dataset.sectionColor);

    const { sectionId, sectionColor } = el.dataset;
    sctionMaps.value.push({
      sectionId,
      sectionColor,
      top: el.getBoundingClientRect().top,
    });
  });
  // console.log(sctionMaps.value);

  window.addEventListener("scroll", obsLink);
  obsLink();
});
onUnmounted(() => {
  window.removeEventListener("scroll", obsLink);
});
</script>

<template>
  <header>
    <div class="header-wrap max-w-[700px]">
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
    @apply w-full px-[50px] pt-[10px] flex justify-between items-center;
  }

  & .logo {
    @apply relative top-[-7px] text-[2em] text-[#fff] font-[700];
  }
}

.header-wrap nav {
  @apply flex gap-[10px];

  .linked {
    @apply relative text-[#fff] font-[600] py-[12px] px-[20px];

    &.active {
      @apply text-[#333] rounded-l-[10px] rounded-r-[10px];

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
