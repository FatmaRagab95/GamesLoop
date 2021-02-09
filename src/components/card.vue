<template>
    <div class="col s12 m3 card-box">
        <div class="card">
            <div class="card-content white-text">
                <div class="img center-align">
                    <img class="responsive-img" src='//via.placeholder.com/200x150' />
                </div>
                <span class="card-title truncate lime-text text-accent-2">{{title}}</span>
                <p class='truncate'>{{body}}</p>
                </div>
                <div class="card-action">
                <router-link :to='{name:"Details", params:{"id": id}}' class='lime-text text-accent-2'>See Details</router-link >
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'card',
    props:['title', 'body', 'id'],
    data() {
        return {

        }
    }
}
</script>

<style>
.card {
    background-color:rgba(0,0,0,.5);
}
</style>