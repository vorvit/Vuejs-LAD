<template>
  <ul class="posts">
    <li
      @click="
        $router.push({
          name: 'post',
          params: {
            id: item.id
          },
          query: $route.query
        })
      "
      :key="item.id"
      v-for="item of data"
    >
      {{ item.id + ' ' + item.title }}
    </li>
  </ul>
</template>

<script setup lang="ts">
import { ref, watchEffect } from 'vue';
//import { posts } from '@/mock/posts';
import { Connect } from '@/connection/ConnectionAxios';

const data = ref<{ [key: string]: any }>([]);
watchEffect(async () => {
  Connect().then((resp) => (data.value = resp.data));
});
</script>

<style src="./PostsView,style.scss" lang="scss" scoped></style>
