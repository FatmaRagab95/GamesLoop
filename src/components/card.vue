<template>
    <div class="col s12 m3 card-box">
        <div class="card">
            <div class="card-content white-text">
                <span class="badge white-text">{{category}}</span>
                <div class="img center-align">
                    <img class="responsive-img" src='https://via.placeholder.com/200x150' />
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
    props:['category', 'title', 'body', 'id' ],
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
.card .badge {
    font-size: 14px;
    margin-top: -33px;
    background-color:#c00;
}
</style>