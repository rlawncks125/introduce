<script setup lang="ts">
const activeClass = ref("Home");
const listMaps = [
  {
    color: "#ff4d4d",
    content: "Home",
  },
  {
    color: "#c56cf0",
    content: "About",
  },
  {
    color: "#ffeaa7",
    content: "Services",
  },
  {
    color: "#17c0eb",
    content: "Portfolio",
  },
  {
    color: "#fd79a8",
    content: "Contact",
  },
];

const activeClassInfo = reactive({
  HTML: "",
  Ratio: 0,
  index: 0,
});

const options: IntersectionObserverInit = {
  root: window.document,
  rootMargin: "0px 0px 0px 0px",
  threshold: [0, 0.1, 0.2, 0.8, 0.9, 0.92, 1],
};
const observerEntity: IntersectionObserverCallback = (entries, observer) => {
  entries.forEach((entry) => {
    const el = entry.target as HTMLElement;

    if (entry.intersectionRatio > 0.01 && entry.intersectionRatio < 0.3) {
      // console.log(
      //   el.dataset.index,
      //   entry.intersectionRatio,
      //   "이하",
      //   activeClassInfo
      // );
      if (el.dataset.index && +el.dataset.index < activeClassInfo.index) {
        activeClass.value = listMaps[+el.dataset.index].content;
        // console.log("교체", activeClass.value);
      }
    }

    if (entry.intersectionRatio > 0.92) {
      activeClass.value = el.innerHTML;

      activeClassInfo.HTML = el.innerHTML;
      activeClassInfo.Ratio = +entry.intersectionRatio;
      activeClassInfo.index = +el.dataset.index!;
      // console.log(
      //   el.dataset.index,
      //   entry.intersectionRatio,
      //   "현재",
      //   activeClassInfo
      // );
    }
  });
};

const observer = new IntersectionObserver(observerEntity, options);

const lists: { color: string; content: string; top: number }[] = [];

document.querySelector("header")?.getBoundingClientRect().bottom || 0;

onMounted(() => {
  const sections = document.querySelectorAll("section");

  sections.forEach((v, index) => {
    observer.observe(v);

    const da = v.getBoundingClientRect().top;
    console.log({ ...listMaps[index], top: da });
    lists.push({ ...listMaps[index], top: da });
  });
});

const moveLiked = (content: string) => {
  const find = lists.filter((v) => v.content === content);
  scrollTo({
    top: find[0].top,
    behavior: "smooth",
  });
};
</script>

<template>
  <header>
    <a href="#" class="logo">Logo</a>
    <nav>
      <div
        @click="moveLiked(item.content)"
        v-for="item in listMaps"
        class="linked cursor-pointer"
        :class="activeClass == item.content ? 'active' : ''"
        :style="`--clr: ${item.color}`"
      >
        {{ item.content }}
      </div>
    </nav>
  </header>
  <section
    v-for="(item, index) in listMaps"
    :data-index="index"
    :id="item.content"
    :style="`--clr: ${item.color}`"
  >
    {{ item.content }}
  </section>
  <section class="text-sm text-black">
    <h1>
      observer 사용시 주의 감지 객체가 100vh 넘어가면 Ratio 값이 0~1 이아니라
      감지 힘듬
    </h1>
  </section>
</template>
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-decoration: none;
  font-family: "Poppins", sans-serif;
  scroll-behavior: smooth;
}
section {
  width: 100%;
  height: 100vh;
  background: var(--clr);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 8em;
  color: rgba(0, 0, 0, 0.25);
  font-weight: 800;
  // text-transform: uppercase;
}
header {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  background: #333;
  padding: 10px 50px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
header .logo {
  position: relative;
  top: -7px;
  font-size: 2em;
  color: #fff;
  font-weight: 700;
}
header nav {
  display: flex;
  gap: 10px;
}
header nav .linked {
  position: relative;
  color: #fff;
  font-weight: 500;
  padding: 12px 20px;
}
header nav .linked.active {
  background: var(--clr);
  color: #333;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
header nav .linked.active::before {
  content: "";
  position: absolute;
  left: -20px;
  bottom: 0;
  width: 20px;
  height: 20px;
  background: transparent;
  border-bottom-right-radius: 20px;
  box-shadow: 5px 5px 0 5px var(--clr);
}
header nav .linked.active::after {
  content: "";
  position: absolute;
  right: -20px;
  bottom: 0;
  width: 20px;
  height: 20px;
  background: transparent;
  border-bottom-left-radius: 20px;
  box-shadow: -5px 5px 0 5px var(--clr);
}
</style>
