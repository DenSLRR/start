<template>
  <div class="p-6">
    <div v-if="props.posts.length <= 0">No posts</div>
    <PostItem v-else @card="$emit('card', post)" @remove="$emit('remove', post)" :key="post.id" v-for="post in props.posts" :post="post"/>
  </div>
</template>

<script setup>
import PostItem from './PostItem.vue';
    const props = defineProps({
      posts: Array,
    })
</script>

<style  scoped>

</style>