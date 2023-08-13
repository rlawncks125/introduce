<script setup lang="ts">
const props = defineProps<{
  // 타이핑 할 텍스트 문자열 배열
  text: Array<any>;
  // 반복 횟수
  iterations?: number;
  // 타이핑 속도
  typeSpeed?: number;
  // 지원지는 속도
  eraseSpeed?: number;
  /* 현재 단어가 다음 단어를 삭제하고 입력하기 전에 화면에 나타나는 시간 **/
  delay?: number;
  // 이전 단어가 완전히 지워진 후 배열에서 다음 단어가 나타나는 시간
  intervals?: number;
  // 애니메이션 시작 시기
  start?: number;
  // 스페이스시 줄바꿈
  spaceNextLine?: boolean;
}>();

const attr = useAttrs();
</script>

<template>
  <VueWriter
    :class="attr.class || ''"
    :array="props.text"
    :iterations="props.iterations || 0"
    :typeSpeed="props.typeSpeed || 200"
    :eraseSpeed="props.eraseSpeed || 100"
    :delay="props.delay || 2000"
    :interval="props.intervals || 500"
    :start="props.start || 0"
  >
    <slot />
  </VueWriter>
</template>

<style lang="scss">
.is-typed {
  @apply text-center;

  & span.typed {
    word-break: keep-all;
    text-align: center;
    word-spacing: v-bind("(props.spaceNextLine ? '100vw' : 'noraml')");
  }

  & span.cursor {
    @apply bg-black;
    animation: blink 1s infinite;
  }
}
@keyframes blink {
  49% {
    background-color: black;
  }
  50% {
    background-color: transparent;
  }
  99% {
    background-color: transparent;
  }
}
</style>
