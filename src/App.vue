<template>
  <div>

    <h1>Faker</h1>

    <p>Total likes: {{ totalLikes }}</p>

    <div class="flex">
      
      <div class="w-40 form">

        <h2>Filter</h2>

        <input type="number" v-model.number="filterCount" placeholder="Like count" />

        <h2>Add a tweet</h2>

        <form v-on:submit.prevent="addNewTweet">

          <label for="tweet_name">Name:</label>
          <input type="text" id="tweet_name" v-model="newTweet.name" placeholder="Name" />
          <br />

          <label for="tweet_handle">Handle:</label>
          <input type="text" id="tweet_handle" v-model="newTweet.handle" placeholder="Handle" />
          <br />

          <label for="tweet_handle">Tweet:</label>
          <input type="text" id="tweet_text" v-model="newTweet.tweet" placeholder="Tweet text" />
          <br />

          <label for="tweet_handle">Likes:</label>
          <input type="number" id="tweet_text" v-model.number="newTweet.likes" placeholder="Likes" min="0"/>
          <br />

          <input type="submit" value="Add tweet" />

        </form>

      </div>

      <div class="w-60">
        <ul>
          <tweet-list-item v-for="(tweet, index) in filterTweets" :key="index" :data="tweet"></tweet-list-item>
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
      ],
      newTweet: {
        id: null,
        name: '',
        handle: '',
        img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
        tweet: '',
        likes: 0
      },
      filterCount: 0
    }
  },
  computed: {
    totalLikes: function(){
      return this.tweets.reduce((total, tweet) => total + tweet.likes, 0);
    },
    filterTweets: function(){
      return this.tweets.filter((tweet) => tweet.likes >= this.filterCount);
    }
  },
  methods: {
    addNewTweet: function(){
      this.newTweet.id = this.tweets.length + 1;
      this.tweets.push(this.newTweet);

      this.newTweet = {
        id: null,
        name: '',
        handle: '',
        img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
        tweets: '',
        likes: 0
      }
    }
  },
  components: {
    'tweet-list-item': tweetListItem
  }
}
</script>

<style>
*{
  font-family: 'Alata', sans-serif;
}
body{
  text-align: center;
}
ul{
  margin: 0;
  padding: 0;
  list-style-type: none;
}
h1, h2{
  color: rgb(29,161,242);
}

.flex{
    display: flex;
    align-items: flex-start;
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

.form{
  margin-right: 20px;
  background: rgb(225,232,237);
}
label{
  width: 20%;
}
input{
  margin: 10px;
  padding: 10px 5px;
  width: 80%;
  border: 3px solid transparent;
}
input[type=submit]{
  background: rgb(29,161,242);
  color: rgb(255, 255, 255);
}

input:focus{
  outline: none;
  border: 3px solid rgb(29,161,242);
}
input[type=submit]:hover{
  cursor: pointer;
}
</style>