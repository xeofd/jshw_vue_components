<template>
  <li :class="listItemClass">
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
    props: ['data'],
    computed: {
        listItemClass: function(){
            if (this.data.likes > 10){
                return 'tweet-layout highlighted';
            } else{
                return 'tweet-layout';
            }
        }
    }
}
</script>

<style scoped>
.tweet-layout{
    margin: 10px auto;
    background: rgb(245,248,250);
}
img{
    width: 100%;
}

.highlighted{
    background: rgb(29,161,242);
    color: rgb(255, 255, 255);
}
</style>