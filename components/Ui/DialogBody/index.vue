<template>
  <div class="dialog-body" tabindex="-1" ref="dialogBody"
    v-on:blur="onDialogBodyBlur"
  >
    <slot />
  </div>
</template>

<script>
  export default {
    name: 'UiDialogBody'
  }
</script>

<script setup>
  import { ref, defineProps, defineEmits, toRefs, watch, nextTick, onMounted } from 'vue'

  const props = defineProps( {
    modelValue: {
      type: Boolean
    }
  } )

  const emit = defineEmits( [ 'update:modelValue' ] )

  const { modelValue } = toRefs( props )

  const dialogBody = ref( null )

  const modelValueWatchHandler = () => {
    if ( modelValue.value ) {
      document.body.style.overflowY = 'hidden'
      nextTick( () => dialogBody.value.focus() )
    } else {
      document.body.style.overflowY = null
    }
  }

  onMounted( () => {
    modelValueWatchHandler()
  } )

  watch( modelValue, modelValueWatchHandler )

  const onDialogBodyBlur = () => emit( 'update:modelValue', false )
</script>