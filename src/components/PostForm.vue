<template>
    <form @submit.prevent >
      <h1>Create POST</h1>
      <input v-model="state.title"  class="bg-green-900 rounded-lg p-5 mb-4 mr-5" type="text" placeholder="Name">
      <input v-model="state.body" class="bg-green-900 rounded-lg p-5 mb-4" type="text" placeholder="Description">
      <button @click="createPost" class=" p-3 ml-2 bg-green-900 rounded-lg " >SEND</button>
    </form>
</template>

<script setup>
    import { ref,defineEmits } from 'vue';

    const state = ref({
      title: '',
      body: '',
    })

    
  const emits = defineEmits();

  function createPost () { 

  
    const newPost = {
      id: Date.now(),
      title: state.value.title,
      body: state.value.body
    }

    if(newPost.title !== '' && newPost.body !== '') {
      emits('create-post', newPost)
    } else {
      alert('Invalid data')
    }



  state.value.title = ''
  state.value.body = ''
  }


</script>

<style  scoped>

</style>