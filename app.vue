<template>
  <div>
    <ClientOnly>
      <NuxtLayout>
        <NuxtPage :key="$route.fullPath" />
      </NuxtLayout>
    </ClientOnly>
  </div>
</template>

<style lang="scss">
@font-face {
  font-family: "DNFForgedBlade";
  font-style: normal;
  font-weight: 300;
  src: url("//cdn.df.nexon.com/img/common/font/DNFForgedBlade-Light.otf")
    format("opentype");
}

@font-face {
  font-family: "DNFForgedBlade";
  font-style: normal;
  font-weight: 500;
  src: url("//cdn.df.nexon.com/img/common/font/DNFForgedBlade-Medium.otf")
    format("opentype");
}

@font-face {
  font-family: "DNFForgedBlade";
  font-style: normal;
  font-weight: 700;
  src: url("//cdn.df.nexon.com/img/common/font/DNFForgedBlade-Bold.otf")
    format("opentype");
}
</style>
