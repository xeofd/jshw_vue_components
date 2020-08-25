<template>
  <li class="tweet-layout">
      <div class="flex">
          <div class="w-20">
              <img :src="data.img" />
          </div>
          <div class="w-80">
              <p>{{ data.name }} | {{ data.likes }} LIKES</p>
              <p>{{ data.handle }}</p>
              <p>{{ data.tweet }}</p>
          </div>
      </div>   
  </li>
</template>

<script>
export default {
    name: 'tweetListItem',
    props: ['data']
}
</script>

<style scoped>
.tweet-layout{
    margin: 10px auto;
    background: rgb(228, 228, 228);
}
img{
    width: 100%;
}
</style>