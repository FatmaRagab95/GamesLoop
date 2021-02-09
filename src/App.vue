<template>
  <div id="app">
    <navLayout/>
      <router-view/>
    <footerLayout/>
  </div>
</template>

<script>

import navLayout from '@/components/layout/navbar'
import footerLayout from '@/components/layout/footer'


export default {
  name: 'App',
  components: {navLayout, footerLayout},
  methods: {
    update() {
      setTimeout(function () {
        $('.variable-width').slick({
          dots: false,
          infinite: true,
          speed: 300,
          slidesToShow: 5,
          centerMode: true,
          variableWidth: true,
          slidesToShow: 3,
          slidesToScroll: 1,
          autoplay: true,
          autoplaySpeed: 2000,
        });
    
      }, 1000);
      window.scroll({
        top: 0,
      });
    }
  },
  watch: {
      $route: 'update'
  },
  created () {
    $(document).ready(function() {
        $('.variable-width').slick({
          dots: false,
          infinite: true,
          speed: 300,
          slidesToShow: 5,
          centerMode: true,
          variableWidth: true,
          slidesToShow: 3,
          slidesToScroll: 1,
          autoplay: true,
          autoplaySpeed: 2000,
        });
    });
  }
}
</script>

<style>

/* global rules*/
body {
  font-family: 'Tajawal', sans-serif;
  line-height:2;
  background-color:#f4f4f4;
}
a, a:hover {
  color:inherit
}
.btn, .btn-large, .btn-small {
    background-color: #ea1e2e;
}
.btn:hover, .btn-large:hover, .btn-small:hover {
  background-color:#ea1e2e;
  opacity: .8;
}
.group-section {
  margin-bottom:60px;
  background-color:#fff;
  box-shadow:0 0 5px #eee;
  padding-bottom:30px;
}

</style>
