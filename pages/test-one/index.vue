<template>
  <div>
    <div class="content">
      <button
        v-on:click="activeFirst = true"
      >
        <span>Открыть</span>
      </button>

      <div>
        <button
          v-on:click="activeSecond = true"
        >
          <span>Открыть</span>
        </button>
      </div>

      <ui-dialog v-model="activeFirst">
        <h1>Первое диалоговое окно (справа)</h1>
      </ui-dialog>

      <ui-dialog-left v-model="activeSecond">
        <h1>Второе диалоговое окно (слева)</h1>
      </ui-dialog-left>
    </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue'

  import UiDialog from '@/components/Ui/Dialog'
  import UiDialogLeft from '@/components/Ui/Dialog/Left'

  const activeFirst = ref( false )
  const activeSecond = ref( false )
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