<script setup lang="ts">
definePageMeta({
  layout: "active-link-page-scroll",
});
</script>

<template>
  <ActiveLinkPageScrollSection
    class="h-[50vh]"
    bg-color="#ff4d4d"
    section-id="소개"
  >
    <div
      class="max-w-[1200px] h-full flex flex-col justify-center items-center"
    >
      <h2 class="text-white text-[1.2rem]">저를 소개합니다.</h2>
      <div class="w-[80%] h-[80%] bg-slate-50 rounded-xl p-4">hi</div>
    </div>
  </ActiveLinkPageScrollSection>
  <ActiveLinkPageScrollSection
    class="h-[100vh]"
    bg-color="#c56cf0"
    section-id="정보"
  >
    섹션 테스트2
  </ActiveLinkPageScrollSection>
  <ActiveLinkPageScrollSection
    class="h-[100vh]"
    bg-color="#ff4aaa"
    section-id="포트폴리오"
  >
    섹션 테스트3
  </ActiveLinkPageScrollSection>
  <section class="h-[100vh]">그냥 섹션 안잡힘</section>
</template>

<style lang="scss"></style>
