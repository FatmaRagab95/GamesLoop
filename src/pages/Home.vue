<template>
  <div class="home">
    <headerLayout/>

    <div class='container'>
      <div class='group-section'>
          <div class='layout'>
            <div class="row">
              <div class="col l8">
                <div class='featured-img responsive-img'>
                  <img src='../assets/Bitmap@1X(14).png'/>
                </div>
              </div>
              <div class="col l4">
                <div class='txt'>
                  <h3>Subway Surfers</h3>
                  <p>SURF the urban wave!
                      DODGE the oncoming trains!
                      GRIND trains with your cool… crew of friends!

                      Run as far as you can on the endless train tracks with your friends Jake, Tricky & Fresh whilst attempting to escape from the Inspector and his fast paced dog… Read more.</p>
                      <span class='grey-text'>300 Downloads</span>
                </div>
              </div>
            </div>
          </div>
      </div>

      <div class='group-section'>
          <h3>Most Recommended</h3>
          <div class='layout'>
            <div class="row">
              <card v-for='(game,i) in data.slice(0,4)' :key='game.id' :i='i' :id='game.id' :title='game.title' :body='game.body'  :category='game.category'></card>
            </div>
            <div class="center-align">
              <a class="waves-effect waves-light btn">See More</a>
            </div>
          </div>
      </div>

      <div class='group-section'>
          <h3>Most Popular</h3>
          <div class='layout'>
            <div class="row">
              <card v-for='(game,i) in data.slice(0,4)' :key='game.id' :i='i' :id='game.id' :title='game.title' :body='game.body' :category='game.category'></card>
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
.home h3 {
  font-size:22px;
  padding:30px 30px 0 30px;
}
.home .featured-img {
  padding:30px 30px 0 30px;
}
.home .featured-img img {
  max-width:100%;
}
@media only screen and (max-width: 767px) {
  .home h3 {
    font-size:16px;
  }
}
</style>
