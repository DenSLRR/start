<template>
   <div @click="onClose" class="fixed h-full w-full bg-black bg-opacity-50 top-0 bottom-0 right-0 left-0 top-0 flex justify-center items-center">
        <div @click.stop="hideDialog" class=" flex justify-center items-center bg-red-900 w-1/4 h-72 rounded-3xl ">
        <slot></slot>
    </div>
   </div>
</template>

<script setup>
     const props = defineProps({
      show: {
        type: Boolean,
        default: false
      }
    })

    
    const emits = defineEmits("onClose");

    // function hideDialog() {
    //     $emit('update:show', false)
    // }

    function onClose() {
        emits('onClose')
    }

</script>

<style  scoped>

</style>