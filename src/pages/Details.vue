<template>
    <div class="details">

        <!-- start detials layout -->
        <div class="details-layout">
            <div class="container">
                <div class="row">
                    <div class="col l4 s12">
                        <div class="img">
                            <div class="slider">
                                <ul class="slides">
                                <li>
                                    <img :src="img">
                                </li>
                                <li>
                                    <img src="https://via.placeholder.com/500">
                                </li>
                                <li>
                                    <img src="https://via.placeholder.com/500">
                                </li>
                                <li>
                                    <img src="https://via.placeholder.com/500">
                                </li>
                                </ul>
                            </div>
                        </div>
                    </div>
                    <div class="col l8 s12">
                        <div class="txt-container">
                            <div class="txt white-text">
                                <div class='desc'>
                                    <h2 class='lime-text text-accent-2'>Title:</h2>
                                    <p>{{title}}</p>
                                </div>
                            </div>

                            <div class="txt white-text" v-show='body.length > 0'>
                                <div class='desc'>
                                    <h2 class='lime-text text-accent-2'>Description:</h2>
                                    <p>{{body}}.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- end details layout -->

        <!-- start recomended section -->
        <div class='group-section'>
            <div class='container'>
                <h3 class='mainFont lime-text text-accent-2'>
                 Recomended
                </h3>
                <div class='layout'>
                <div class="row">
                    <card v-for='game in recomended.slice(0,8)' :key='game.id' :id='game.id' :title='game.title' :body='game.body' :category='game.category'></card>
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

    import axios from 'axios';
    import card from '../components/card.vue';
    export default {
        name:'details',
        components: {card},
        data() {
            return {
                title:'',
                body: '',
                img:'',
                recomended: []
            }
        },
        watch: {
            $route: 'getDetails'
        },
        methods: {
            txtAnimation (txt,x) {
                let that = this;
                that[x] = '';
                for (let i = 0; i < txt.length; i++) {
                    setTimeout(function () {
                        that[x] =  that[x] + txt[i];
                    }, 10 * (i + 1));
                }
            },
            getDetails() {
                let that = this;
                let gameId = that.$route.params.id;
                axios.get(`https://api.jsonbin.io/b/602202ebd5aafc6431a60c88/2`)
                .then((response) => {
                    response.data = response.data.filter(x => x.id == gameId)
                    that.img = response.data[0].img;
                    that.txtAnimation(response.data[0].title, 'title');
                    setTimeout(function () {
                    that.txtAnimation(response.data[0].body, 'body');
                    }, 10 * (response.data[0].title.length));
                });
            }
        },
        created() {
            let that = this;
            that.getDetails();

            axios.get(`https://api.jsonbin.io/b/602202ebd5aafc6431a60c88/2`)
            .then((response) => {
                that.recomended = response.data
            });

            $(document).ready(function() {
                $('.slider').slider();
            });
        }
    }
</script>

<style>
.details .details-layout {
  background:linear-gradient(rgba(0, 51, 204,.2),rgba(0, 51, 204,.2)), url('../assets/pic_01.png') fixed;
  padding-top:60px;
  padding-bottom:60px;
}
.details .details-layout .slider {
    height:340px !important;
}
.details .details-layout .slider .slides {
    height:300px !important;
}
.details .img, .details .txt-container .txt {
    background-color:rgba(0,0,0,.5);
    padding:15px;
    margin:30px auto;
}
.details .img {max-width:300px;}
.details .txt-container .img img {
    margin:auto;
}
.details .txt-container .txt h2 {
    font-size:22px;
}
.details .group-section {margin-top:60px;}
.details .group-section h3 {
  font-size:22px;
  padding-left:45px;
  position:relative;
}
.details h3:before {
  content:'';
  position: absolute;
  width:45px;
  height:45px;
  top: -9px;
  left: 0px;
  background:url('../assets/heart.png') no-repeat;
  background-position:0 0;
}
</style>