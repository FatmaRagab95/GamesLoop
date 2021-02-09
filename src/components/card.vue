<template>
    <div class="col s12 l3 m6 card-box">
        <div class="card white">
            <div class="card-content">
                <router-link :to='{name:"Details", params:{"id": id}}'>
                    <div class="img center-align">
                        <img v-if='i == 0' class="responsive-img" src='../assets/0.png' />
                        <img v-else-if="i == 1" class="responsive-img" src='../assets/1.png' />
                        <img v-else-if="i == 2" class="responsive-img" src='../assets/2.png' />
                        <img v-else-if="i == 3" class="responsive-img" src='../assets/3.png' />
                    </div>
                    <span class="card-title truncate">{{title}}</span>
                    <p class='truncate'>{{body}}</p>
                    <span class="chip yellow">{{category}}</span>
                </router-link >
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'card',
    props:["i", 'category', 'title', 'body', 'id' ],
    data() {
        return {

        }
    }
}
</script>

<style>
.card {
    background-color:rgba(0,0,0,.5);
    padding-top:0;
    box-shadow:0 0 1px #ccc;
}
</style>