<template>
  <div>
    <ClientOnly>
      <NuxtLayout>
        <NuxtPage :key="$route.fullPath" />
      </NuxtLayout>
    </ClientOnly>
  </div>
</template>
