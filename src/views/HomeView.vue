<template>
  <div class="home">
    <div class="container-title">
      <h1>Posts</h1>
    </div>
    <CardPosts />
  </div>
</template>

<script>

import CardPosts from '@/components/CardPosts.vue';

export default {
  name: 'HomeView',

  components: {
    CardPosts
  }
}
</script>

<style scoped>

  .container-title{
    padding: 20px 50px;
  }
  .home{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

</style>
