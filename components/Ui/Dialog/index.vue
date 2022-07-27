<template>
  <ui-overlay
    v-show="modelValue"
  >
    <div class="wrapper">
      <div class="dialog" tabindex="-1" ref="dialog"
        v-on:blur="onDialogBlur"
      >
        <slot />
      </div>
    </div>
  </ui-overlay>
</template>

<script setup>
  import { defineProps, defineEmits, toRefs, watch, onMounted, nextTick } from 'vue'
  import UiOverlay from '@/components/Ui/Overlay'

  const props = defineProps( {
    modelValue: {
      type: Boolean
    }
  } )

  const emit = defineEmits( [ 'update:modelValue' ] )

  const { modelValue } = toRefs( props )
  const dialog = ref( null )

  const modelValueWatchHandler = () => {
    if ( modelValue.value ) {
      document.body.style.overflowY = 'hidden'
      nextTick( () => {
        dialog.value.focus()
      } )
    }
    else document.body.style.overflowY = 'inherit'
  }

  watch( modelValue, modelValueWatchHandler )

  const onDialogBlur = () => {
    emit( 'update:modelValue', false )
  }

  onMounted( () => {
    modelValueWatchHandler()
  } )
</script>

<style scoped>
  .wrapper {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .dialog {
    width: 100px;
    height: 100px;
    background-color: white;
  }
</style>