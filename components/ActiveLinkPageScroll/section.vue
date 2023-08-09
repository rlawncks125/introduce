<script setup lang="ts">
const props = defineProps<{
  sectionId: string;
  bgColor: string;
}>();
const attrs = useAttrs();
</script>

<template>
  <section
    :data-section-id="props.sectionId"
    :data-section-color="props.bgColor"
    :class="attrs.class"
    :style="`--clr:${props.bgColor}`"
  >
    <slot />
  </section>
</template>

<style lang="scss">
section {
  @apply w-full;
  background: var(--clr);
}
</style>
