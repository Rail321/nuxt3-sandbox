<template>
  <div class="overlay">
    <slot />
  </div>
</template>

<style scoped>
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(33, 32, 34, .7);
  }
</style>