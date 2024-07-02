<template>
  <button @click="showDialog"  class=" p-3 ml-2 mt-6 mb-6 ml-24 bg-green-900 rounded-lg " >Create User</button>
  
  <PostList  @remove="removePost" :posts="posts"/>
    <MyDialog @on-close="dialogVisible = false" v-if="dialogVisible">
      <PostForm @create-post='createPost'/>
    </MyDialog>
</template>

<script setup>
import {ref} from 'vue'

import PostList from './components/PostList.vue';
import PostForm from './components/PostForm.vue'
import MyDialog from './components/MyDialog.vue';



const posts = ref([
  {id:1, title: 'Post o java', body: 'sfdffdsfsdfsdfsdfsd'},
  {id:2, title: 'Post o javaScript', body: 'sfdffdsfsdfsdfsdfsd'},
  {id:3, title: 'Post o Python', body: 'sfdffdsfsdfsdfsdfsd'},
  {id:4, title: 'Post o C#', body: 'sfdffdsfsdfsdfsdfsd'}
])


const dialogVisible = ref(false)
// const emits = defineEmits();



function createPost(post) {
  posts.value.push(post)
  dialogVisible.value = false

}

function removePost(post) {
  posts.value = posts.value.filter(p => p.id !== post.id)
}

function showDialog() {
  dialogVisible.value = true
}




</script>

<style scoped></style>
