<script setup lang="ts">
const activeClass = ref("Home");
const listMaps = [
  {
    color: "#ff4d4d",
    contentID: "Home",
    content: "Home-content",
  },
  {
    color: "#c56cf0",
    contentID: "About",
    content: "About-content",
  },
  {
    color: "#ffeaa7",
    contentID: "Services",
    content: "Services",
  },
  {
    color: "#17c0eb",
    contentID: "Portfolio",
    content: "Portfolio-content",
  },
  {
    color: "#fd79a8",
    contentID: "Contact",
    content: "Contact-content",
  },
];

const lists: { color: string; contentID: string; top: number }[] = [];
const navHegiht = ref(0);

document.querySelector("header")?.getBoundingClientRect().bottom || 0;
const obsLink = () => {
  let catchC = "";
  const catchScroll = scrollY + navHegiht.value;
  lists.reduce((a, b) => {
    if (a.top <= catchScroll && catchScroll < b.top) {
      catchC = a.contentID;
    }
    return b;
  }, lists[0]);
  activeClass.value = catchC || lists[lists.length - 1].contentID;
  console.log(catchScroll, catchC, scrollY);
};

onMounted(() => {
  const sections = document.querySelectorAll("section");
  navHegiht.value =
    document.querySelector("header")?.getBoundingClientRect().bottom || 0;

  sections.forEach((v, index) => {
    // observer.observe(v);
    const da = v.getBoundingClientRect().top;
    console.log({ ...listMaps[index], top: da });
    lists.push({ ...listMaps[index], top: da });
  });

  window.addEventListener("scroll", obsLink);
});
onUnmounted(() => {
  window.removeEventListener("scroll", obsLink);
});

const moveLiked = (contentID: string) => {
  const find = lists.filter((v) => v.contentID === contentID);
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
        @click="moveLiked(item.contentID)"
        v-for="item in listMaps"
        class="linked cursor-pointer"
        :class="activeClass == item.contentID ? 'active' : ''"
        :style="`--clr: ${item.color}`"
      >
        {{ item.contentID }}
      </div>
    </nav>
  </header>
  <section
    v-for="(item, index) in listMaps"
    :data-index="index"
    :id="item.contentID"
    :style="`--clr: ${item.color}`"
  >
    {{ item.content }}
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
  height: 150vh;
  background: var(--clr);
  display: flex;
  justify-contentcontentid: center;
  align-items: center;
  font-size: 8em;
  color: rgba(0, 0, 0, 0.25);
  font-weight: 800;
  text-transform: uppercase;
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
