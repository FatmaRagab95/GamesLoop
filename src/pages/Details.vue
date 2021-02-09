<template>
    <div class="details">
        <div class="container">
            <!-- start detials layout -->
            <div class="details-layout group-section">
                <div class="img">
                    <img class='responsive-img' src="../assets/Bitmap@1X(14).png">
                </div>

                <div class="row">
                    <div class="col l8 s12">
                        <div class="txt-container">
                            <div class="txt" v-show='body.length > 0'>
                                <h1>{{title}}</h1>
                                <div class='desc'>
                                    <h2>Description:</h2>
                                    <p>{{body}}.</p>
                                </div>
                                <a class='waves-effect waves-light btn'>Read More</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- end details layout -->

            <!-- start recomended section -->
            <div class='group-section'>
                <h3>
                    Recomended
                </h3>
                <div class='layout'>
                    <div class="row">
                        <card v-for='(game,i) in recomended.slice(0,4)' :key='game.id' :i='i' :id='game.id' :title='game.title' :body='game.body' :category='game.category'></card>
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
            getDetails() {
                let that = this;
                let gameId = that.$route.params.id;
                axios.get(`https://api.jsonbin.io/b/602202ebd5aafc6431a60c88/2`)
                .then((response) => {
                    response.data = response.data.filter(x => x.id == gameId)
                    that.img = response.data[0].img;
                    that.title = response.data[0].title;
                    that.body = response.data[0].body;
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
  padding:15px 15px 30px 15px;
}
.details .img {max-width:100%; text-align: center;}
.details .txt-container .img img {
    margin:auto;
}
.details .txt-container .txt {
    margin-left:30px;
}
.details .txt-container .txt h1 {
    font-size:28px;
}
.details .txt-container .txt h2 {
    font-size:22px;
}
.details .group-section {margin-top:60px;}
.details .group-section h3 {
  font-size:22px;
  padding-left:45px;
  position:relative;
  padding-top:30px;
}
.details h3:before {
  content:'';
  position: absolute;
  width:45px;
  height:45px;
  top: -9px;
  left: 0px;
  background-position:0 0;
}
</style>