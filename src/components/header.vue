<template>
    <header>
      <div class='layout'>

        <div class="txt">
          <div class='container'>
            <h1 class='lime-text text-accent-2'>Welcome,</h1>
            <p>quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam.</p>
          </div>
        </div>

        <!-- start categories -->
        <div class='cats center-align'>
          <div class="carousel lime-text text-accent-2">
            <a class="carousel-item" href="#one!">
              <div class='text-align-center img'>
                <img src='../assets/2.png' />
              </div>
              Adventure Games <span></span>
            </a>
            <a class="carousel-item" href="#two!">
              <div class='text-align-center img'>
                <img src='../assets/3.png' />
              </div>
              Action Games <span></span></a>
            <a class="carousel-item" href="#three!">
              <div class='text-align-center img'>
                <img src='../assets/heels.png' />
              </div>
              Dress Up Games <span></span></a>
            <a class="carousel-item" href="#four!">
              <div class='text-align-center img'>
                <img src='../assets/4.png' />
              </div>
              Race Games <span></span></a>
            <a class="carousel-item" href="#five!">
              <div class='text-align-center img'>
                <img src='../assets/1.png' />
              </div>
              Sports Games <span></span></a>
          </div>
        </div>
      </div>
    </header>
</template>

<script>

export default {
  name: 'headerLayout',
  data () {
    return {
    }
  },
}
</script>

<style>
.home header {
  background:linear-gradient(rgba(0, 51, 204,.2),rgba(0, 51, 204,.2)), url('../assets/pic_01.png')  fixed;
  padding-top:30px;
}
.home header .layout {
  height:100%;
  background:url('../assets/floor06.png') no-repeat center bottom;
  background-size:contain;
  padding-bottom:300px;
}
.home header .layout .txt p {
  max-width:450px;
  color:#fff
}
.home header .cats p {
  max-width:300px;
  margin:30px auto;
}
.home header .carousel {
    height: 400px;
}
.home header .cats .carousel-item {
  height:auto;
  font-size: 18px;
  width:300px;
}
.home header .cats a img {
  max-width:150px;
}
.home header .cats a span {
  background:url('../assets/navi-bg.png') no-repeat center;
  background-size:contain;
  display: block;
  height:80px;
}
</style>