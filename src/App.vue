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
        $('.slider').slider();
        $('.carousel').carousel({
          indicators: true,
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
        $('.slider').slider();
        $('.carousel').carousel({
          indicators: true,
        });
    });
  }
}
</script>

<style>

/* global rules*/
body {
  background-color:#000;
  font-family: 'Play', sans-serif;
  line-height:2;
}
a, a:hover {
  color:inherit
}
.mainFont {
  font-family: 'Press Start 2P', cursive;
}
.rounded-circle {
  border-radius:50%;
}

.group-section {
  background:url('assets/floor08.png') no-repeat bottom;
  margin-bottom:120px;
}
.group-section .layout {
  padding:30px;
  margin-top:60px;
  background:linear-gradient(rgba(0, 51, 204,.2),rgba(0, 51, 204,.2)), url('assets/pic_01.png') fixed;
}
.group-section .layout .btn{
  background-color:#c00;
}
/*global responsive*/
@media screen and (min-width:993px) {
  .container {
    width:85%;
  }
}
</style>
