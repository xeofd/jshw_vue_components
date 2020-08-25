<template>
  <div>

    <h1>Faker</h1>

    <p>Total likes: {{ totalLikes }}</p>

    <div class="flex">
      
      <div class="w-40"></div>

      <div class="w-60">
        <ul>
          <tweet-list-item v-for="(tweet, index) in tweets" :key="index" :data="tweet"></tweet-list-item>
        </ul>
      </div>

    </div>

  </div>
</template>

<script>
// Import
import tweetListItem from './components/tweetListItem';

// Create app component
export default {
  name: 'app',
  data() {
    return {
      tweets:[
        {
          id: 1,
          name: 'James',
          handle: '@jokerjames',
          img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
          tweet: "If you don't succeed, dust yourself off and try again.",
          likes: 10,
        },
        {
          id: 2,
          name: 'Fatima',
          handle: '@fantasticfatima',
          img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
          tweet: 'Better late than never but never late is better.',
          likes: 12,
        },
        {
          id: 3,
          name: 'Xin',
          handle: '@xeroxin',
          img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
          tweet: 'Beauty in the struggle, ugliness in the success.',
          likes: 18,
        }
      ]
    }
  },
  computed: {
    totalLikes(){
      return this.tweets.reduce((total, tweet) => total + tweet.likes, 0);
    }
  },
  components: {
    'tweet-list-item': tweetListItem
  }
}
</script>

<style>
body{
  text-align: center;
  font-family: 'Alata', sans-serif;
}
ul{
  margin: 0;
  padding: 0;
  list-style-type: none;
}

.flex{
    display: flex;
}
.w-20{
    width: 20%;
}
.w-40{
  width: 40%;
}
.w-60{
  width: 60%;
}
.w-80{
    width: 80%;
}
</style>