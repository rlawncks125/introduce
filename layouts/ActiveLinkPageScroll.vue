<script setup lang="ts"></script>

<template>
  <div>
    <!-- <ActiveLinkPageScrollNav /> -->
    <ActiveLinkPageScrollNavObs />
    <slot />
  </div>
</template>

<style lang="scss">
* {
  @apply m-0 p-0 scroll-smooth box-border;

  text-decoration: none;
  // font-family: "Poppins", sans-serif;
  font-family: "DNFForgedBlade", "Poppins", sans-serif;
}
</style>
