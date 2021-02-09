<template>
  <div class="home">
    <headerLayout/>

    <div class='group-section'>
      <div class='container'>

        <div class='white-text filter'>
          <form @submit.prevent>
              <div class="input-field col s12">
                <h4>Filtered By:</h4>
                <select v-model='filter'>
                  <option value="">All</option>
                  <option value="Adventure">Adventure</option>
                  <option value="Action">Action</option>
                  <option value="Dress Up">Dress Up</option>
                  <option value="Race">Race</option>
                  <option value="Sports">Sports</option>
                </select>
              </div>
          </form>
        </div>

        <h3 class='mainFont lime-text text-accent-2'>
          Featured Games
        </h3>
        <div class='layout'>
          <div class="row">
            <card v-for='game in data.slice(0,4)' :key='game.id' :id='game.id' :title='game.title' :body='game.body'  :category='game.category'></card>
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
            <card v-for='game in data.slice(0,4)' :key='game.id' :id='game.id' :title='game.title' :body='game.body'  :category='game.category'></card>
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
            <card v-for='game in data.slice(0,4)' :key='game.id' :id='game.id' :title='game.title' :body='game.body' :category='game.category'></card>
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
      data:[],
      filter: ''
    }
  },
  watch: {
      '$store.state.cat': function () {
        this.filter = this.$store.state.cat;
      },
      filter: 'updateCat',
  },
  methods: {
    updateCat() {
        let that = this;
        this.$store.state.cat = this.filter;
        if (that.filter != '') {
          axios.get('https://api.jsonbin.io/b/602202ebd5aafc6431a60c88/2')
          .then((response) => {
            that.data = response.data.filter(x => x.category == that.filter);
          });
        } else {
          axios.get('https://api.jsonbin.io/b/602202ebd5aafc6431a60c88/2')
          .then((response) => {
            that.data = response.data;
          });
      }
    }
  },
  created() {
    this.filter = this.$store.state.cat ? this.$store.state.cat : '';
    this.updateCat()
  }
}
</script>

<style>
.filter {
  max-width:150px;
  margin:0 1px 0 auto
}
.filter h4 {
  font-size:22px;
}
.select-wrapper input.select-dropdown {
    background-color: #fff;
    display: inline-block;
    padding:0 10px;
}
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
