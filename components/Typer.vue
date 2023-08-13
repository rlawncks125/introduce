<script setup lang="ts">
const props = defineProps<{
  text: Array<string>;
  speed: number;
}>();
const writeHTML = ref<HTMLDivElement>();

//
const pEL = ref<HTMLSpanElement>();
let arrayIndex = 0;
let stringIndex = 0;
let invervalIndex: NodeJS.Timer;

//
const createNewSpan = () => {
  const childEl = document.createElement("p");
  pEL.value = childEl;

  writeHTML.value?.appendChild(childEl);
};

const addCountingString = () => {
  if (pEL.value) {
    const nextString = props.text[arrayIndex][stringIndex];
    pEL.value.innerHTML += nextString;

    stringIndex++;

    if (stringIndex === props.text[arrayIndex].length) {
      if (arrayIndex === props.text.length - 1) {
        // 스탑
        clearInterval(invervalIndex);
      } else {
        // 다음 줄
        createNewSpan();
        arrayIndex++;
        stringIndex = 0;
      }
    }
  } else {
    createNewSpan();
  }
};

onMounted(() => {
  invervalIndex = setInterval(addCountingString, props.speed);
});
</script>

<template>
  <div ref="writeHTML" class="writeHTML"></div>
</template>

<style lang="scss">
.writeHTML {
  & p:last-child {
    // 커서
    &::after {
      content: "\00a0";
      display: inline-block;
      background-color: black;
      width: 4px;
      margin-left: 0.2rem;

      animation: blink 1s ease-in-out 0s infinite;
    }
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
