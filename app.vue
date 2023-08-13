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
// 네오플 글꼴 라이선스 정책

// Copyright (c) 2023, NEOPLE Inc. (https://www.neople.co.kr),

// with Reserved Font Name ForgedBlade_TTF.ttf, ForgedBlade_OTF.otf, DNFBitBit_ver2_TTF.ttf, DNFBitBit_ver2_OTF.otf.

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
