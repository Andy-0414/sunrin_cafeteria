<template>
<transition name="fade" appear>
    <div class="CafeteriaBox">
        <div id="infomation">
            {{menu.date.toLocaleDateString()}}
        </div>
        <div v-for="i in menu.lunch" :key="i" class="list">
            {{ i }}
        </div>
        <div v-show="!menu.lunch.length" class="list">
            급식이 없습니다.
        </div>
    </div>
</transition>
</template>

<script>
    export default {
        props: {
            menu: Object,
        },
        components: {
        },
        data: () => ({
        }),
        created: function(){
        }
    }
</script>

<style>
    .CafeteriaBox {
        transition: 1s;
        position: relative;

        height: 600px;
        width: 400px;

        margin: 40px;

        overflow: hidden;
        overflow-y: scroll;

        background-color: white;
        border-radius: 10px;

        box-shadow: -5px 5px 20px 1px #AAAAAA;
    }
    #infomation{
        display: flex;
        justify-content: center;
        align-items: center;

        height: 80px;

        font-size: 2em;
        font-weight: 700;
        color: white;

        background-color: #00838f
    }
    .list{
        display: flex;
        justify-content: center;
        align-items: center;

        font-size: 1.2em;
        height: 60px;

        background-color: #4fb4bf22
    }
    .list:nth-child(2n){
        background-color: #4fb4bf11
    }
    
    .fade-enter, .fade-leave-to {
        height: 0;
        box-shadow: none;
        opacity: 0;
    }
</style>