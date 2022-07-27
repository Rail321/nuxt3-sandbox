<template>
  <div v-show="modelValue">
    <ui-overlay-red>
      <div class="wrapper">
        <div class="body">
          <ui-dialog-body v-bind:modelValue="modelValue" v-on:update:modelValue="emit( 'update:modelValue', $event )">
            <slot />
          </ui-dialog-body>
        </div>
      </div>
    </ui-overlay-red>
  </div>
</template>

<script>
  export default {
    name: 'UiDialog'
  }
</script>


<script setup>
  import { defineProps, defineEmits } from 'vue'
  import UiOverlayRed from '@/components/Ui/Overlay/Red'
  import UiDialogBody from '@/components/Ui/DialogBody'

  defineProps( {
    modelValue: {
      type: Boolean
    }
  } )

  const emit = defineEmits( [ 'update:modelValue' ] )
</script>

<style scoped>
  .wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
  }
  
  .body {
    width: 612px;
    max-width: 100%;
    height: 100%;
    background-color: #FFF;
    box-shadow: 0px 24px 44px rgba(0, 0, 0, 0.55);
  }
</style>