<template>
  <div>
    <div class="content">
      <button
        v-on:click="active = true"
      >
        <span>Открыть</span>
      </button>

      <ui-dialog
        v-model="active"
      >
        <span>Слот заполненный контентом</span>
      </ui-dialog>
    </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue'
  import UiDialog from '@/components/Ui/Dialog'

  const active = ref( true )
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>

<style scoped>
  .content {
    min-height: 200vh;
    background-color: antiquewhite;
  }
</style>