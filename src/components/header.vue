<template>
    <header>
      <div class='layout'>
        <!-- start categories -->
        <div class='cats center-align variable-width'>
            <a class="carousel-item" href='#' @click='changeCat("Adventure")'>
               <span class='chip white'>Adventure Games</span>
            </a>
            <a class="carousel-item" href='#' @click='changeCat("Action")'>
               <span class='chip white'>Action Games</span>
            </a>
            <a class="carousel-item" href='#' @click='changeCat("Dress Up")'>
               <span class='chip white'>Dress Up Games</span>
            </a>
            <a class="carousel-item"  href='#' @click='changeCat("Race")'>
               <span class='chip white'>Race Games</span>
            </a>
            <a class="carousel-item" href='#' @click='changeCat("Sports")'>
               <span class='chip white'>Sports Games</span>
            </a>
        </div>
      </div>
    </header>
</template>

<script>
import axios from 'axios'
export default {
  name: 'headerLayout',
  data () {
    return {
    }
  },
  methods: {
    changeCat(x) {
      this.$store.commit('changeCat', x)
    }
  }
}
</script>

<style>
.home header .layout {
  box-shadow: 0 0 2px #ccc;
  padding: 15px;
  overflow:hidden;
  background-color:#fff;
  margin-bottom:60px;
}
.home header .cats p {
  max-width:200px;
  margin:30px auto;
}
.home header .cats .carousel-item {
  width:200px;
}
.home header .cats .carousel-item .chip {
  border:1px solid #ccc;
}
</style>