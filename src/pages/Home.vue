<template>
  <div class="home">
    <headerLayout/>

    <div class='group-section'>
      <div class='container'>
        <h3 class='mainFont lime-text text-accent-2'>
          Featured Games
        </h3>
        <div class='layout'>
          <div class="row">
            <card v-for='game in data.slice(0,4)' :key='game.id' :id='game.id' :title='game.title' :body='game.body'></card>
          </div>
          <div class="center-align">
            <a class="waves-effect waves-light btn">See More</a>
          </div>
        </div>
      </div>
    </div>

    <div class='group-section'>
      <div class='container'>
        <h3 class='mainFont lime-text text-accent-2'>
           Most Recommended
        </h3>
        <div class='layout'>
          <div class="row">
            <card v-for='game in data.slice(0,4)' :key='game.id':id='game.id' :title='game.title' :body='game.body'></card>
          </div>
          <div class="center-align">
            <a class="waves-effect waves-light btn">See More</a>
          </div>
        </div>
      </div>
    </div>

    <div class='group-section'>
      <div class='container'>
        <h3 class='mainFont lime-text text-accent-2'>
           Most Popular
        </h3>
        <div class='layout'>
          <div class="row">
            <card v-for='game in data.slice(0,4)' :key='game.id' :id='game.id' :title='game.title' :body='game.body'></card>
          </div>
          <div class="center-align">
            <a class="waves-effect waves-light btn">See More</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import headerLayout from '@/components/header';
import Card from '../components/card.vue';

export default {
  name: 'Home',
  components: {headerLayout, Card},
  data () {
    return {
      data:[]
    }
  },
  created() {
    let that = this;
    axios.get('http://jsonplaceholder.typicode.com/posts')
    .then((response) => {
      that.data = response.data;
    });
  }
}
</script>

<style>
.home h3 {
  font-size:22px;
  position:relative;
  padding-left:45px;
}
.home h3:before {
  content:'';
  position: absolute;
  width:45px;
  height:45px;
  top: -9px;
  left: 0px;
  background:url('../assets/heart.png') no-repeat;
}
.home .group-section:nth-of-type(1) h3:before {
  background-position:0 0;
}
.home .group-section:nth-of-type(2) h3:before {
  background-position:-45px 0px;
}
.home .group-section:nth-of-type(3) h3:before {
  background-position:-90px 0;
}
@media only screen and (max-width: 767px) {
  .home h3 {
    font-size:16px;
  }
  .home h3 img {
    width:40px;
  }
}
</style>
