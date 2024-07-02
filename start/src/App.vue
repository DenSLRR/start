<template>
  
    
  
  
  
</template>

<script setup>
import {ref} from 'vue'

import PostList from './'

const posts = ref([
  {id:1, title: 'Post o java', body: 'sfdffdsfsdfsdfsdfsd'},
  {id:2, title: 'Post o javaScript', body: 'sfdffdsfsdfsdfsdfsd'},
  {id:3, title: 'Post o Python', body: 'sfdffdsfsdfsdfsdfsd'},
  {id:4, title: 'Post o C#', body: 'sfdffdsfsdfsdfsdfsd'}
])

const state = ref({
  title: '',
  body: '',
})

function createPost() {
  const newPost = {
    id: Date.now(),
    title: state.value.title,
    body: state.value.body
  }

  posts.value.push(newPost)

  state.value.title = ''
  state.value.body = ''
}

</script>

<style scoped></style>
