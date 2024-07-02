<template>
    <div>
      <button @click="showDialog"  class=" p-3 mt-6 mb-6 ml-24 bg-green-900 rounded-lg " >Create User</button>
      <button @click="fetchUsers" class=" p-3  mt-6 mb-6 ml-24 bg-green-900 rounded-lg " >Request</button>
    </div>
  <PostList  @remove="removePost" :posts="posts"/>
    <MyDialog @on-close="dialogVisible = false" v-if="dialogVisible">
      <PostForm @create-post='createPost'/>
    </MyDialog>
    <div class="flex mt-5">
      <div
       class="border p-4" 
       v-for="pageNumber in totalPages" 
       :key="pageNumber"
       :class="{
        'current-page': page === pageNumber
       }"
       @click="changePage(pageNumber)"
       >{{ page }}</div>
    </div>
</template>

<script setup>
import {ref, onMounted} from 'vue'
import axios from 'axios';


import PostList from './components/PostList.vue';
import PostForm from './components/PostForm.vue'
import MyDialog from './components/MyDialog.vue';


onMounted(() => {
  fetchUsers()
})


const posts = ref([])
const page = ref(1)
const limit = ref(10)
const totalPages = ref(0)

const dialogVisible = ref(false)




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

function changePage (pageNumber) {
  page.value = pageNumber
  fetchUsers()
}

async function fetchUsers() {
  try  {
    const res = await axios.get('https://jsonplaceholder.typicode.com/posts', {
      params: {
        _page: page.value,
        _limit: limit.value
      }
    })
    totalPages.value = Math.ceil(res.headers['x-total-count'] / limit.value) 
    posts.value = res.data
  } catch (e) {
    alert('Error')
  }
}
 




</script>

<style scoped>

.current-page {
  border: 1px solid red;
}

</style>
