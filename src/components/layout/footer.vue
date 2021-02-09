<template>
    <div>
        <div class="footerLayout">
            <div class="container">
                <img src='../../assets/skull.png' />
                <h3 class='mainFont'>Game Over!</h3>
                <p class='lime-text text-accent-2'>Made With  &hearts; By Fatma Ragab</p>
            </div>
        </div>
        <div class='white-text footer'>
            <span>Games Loop &copy; {{new Date().getFullYear()}}</span>
        </div>
    </div>
</template>

<script>
export default {
    name:'footerLayout',
    data() {
        return {

        }
    }
}
</script>

<style>
.footerLayout {
    padding:60px 0;
    height:400px;
    position:relative;
    text-align: center;
    color:#c00;
}
.footerLayout:before {
    content:'';
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:url('../../assets/479216be7eb7443c6f03bd7711bfb348bbd34b1c1506db-qPs4Ni_fw1200.png') center;
    background-size:contain;
    opacity:.2
}
.footerLayout h3 {
    background-size:contain;
    text-align:center;
    font-size:16px;
    margin-top:10px;
}
.footerLayout img {
    max-width: 50px;
}
.footerLayout p {
    letter-spacing: 3px;
    margin-top:30px;
}
.footer {
    margin:0 10px;
}
</style>