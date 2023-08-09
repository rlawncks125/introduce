<script setup lang="ts"></script>

<template>
  <div>
    <ActiveLinkPageScrollNav />
    <slot />
  </div>
</template>

<style lang="scss">
* {
  @apply m-0 p-0 scroll-smooth box-border;

  text-decoration: none;
  font-family: "Poppins", sans-serif;
}
</style>
