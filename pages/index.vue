<template>
    <section class="container">
        <cafeteria-box :menu="today" v-if="today" />
        <cafeteria-box :menu="tomorrow" v-if="tomorrow" />
    </section>
</template>

<script>
    import CafeteriaBox from '~/components/CafeteriaBox.vue'
    import axios from 'axios'

    export default {
        components: {
            CafeteriaBox
        },
        data: ()=>({
            today: null,
            tomorrow: null
        }),
        created: function() {
            var nowDate = new Date()
            axios.get("https://schoolmenukr.ml/api/high/B100000658",{
                params : {
                    date: nowDate.getDate()
                    }
                })
            .then(data=>{
                data.data.menu.date = nowDate
                this.today = data.data.menu
            })
            .catch(err=>{
                console.log(err)
            })

            var date = new Date()
            date.setDate( date.getDate() + 1 )
            axios.get("https://schoolmenukr.ml/api/high/B100000658",{
                params : {
                    date: date.getDate()
                    }
                })
            .then(data=>{
                data.data.menu.date = date
                this.tomorrow = data.data.menu
            })
            .catch(err=>{
                console.log(err)
            })
        }
    }
</script>
<style>
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;

        width: 100%;
        height: 100vh;
        overflow: scroll;
        background: #EEEEEE
    }

    ::-webkit-scrollbar { 
        display: none; 
    }
</style>