<template>
    <div class="CafeteriaBox">
        <div id="infomation">
            {{menu.date}}
        </div>
        <div v-for="i in menu.lunch" :key="i" class="list">
            {{ i }}
        </div>
        <div v-show="!menu.lunch.length" class="list">
            급식이 없습니다.
        </div>
    </div>
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
        position: relative;

        height: 600px;
        width: 400px;

        margin: 40px;

        overflow: hidden;
        overflow-y: scroll;

        background-color: white;
        border-radius: 10px;

        box-shadow: -2px 2px 10px 1px #AAAAAA;
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
</style>