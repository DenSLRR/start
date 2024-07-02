<template>
   <div @click="$emit('card', post)" class="flex justify-between bg-green-900 rounded-lg p-10 mb-4">
      <div>
        <div><strong class="mr-10">Name:</strong>{{ props.post.title }} </div>
        <div><strong class="mr-10">Description:</strong>{{ props.post.body }}</div>
      </div>
      <div>
        <button @click="$emit('remove', post)" class="w-24 h-12  rounded-lg bg-yellow-600">delete</button>
      </div>
    </div>
</template>

<script setup>
    
    const props = defineProps({
        post: Object,
    })
   
</script>

<style  scoped>

</style>