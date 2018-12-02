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
            var date = new Date().getDate()
            axios.get("https://schoolmenukr.ml/api/high/B100000658",{
                params : {
                    year: 2018,
                    month: 12,
                    date: date
                    }
                })
            .then(data=>{
                this.today = data.data.menu
            })
            .catch(err=>{
                console.log(err)
            })

            var date = new Date()
            date.setDate( date.getDate() + 1 )
            date = date.getDate()
            axios.get("https://schoolmenukr.ml/api/high/B100000658",{
                params : {
                    year: 2018,
                    month: 12,
                    date: date
                    }
                })
            .then(data=>{
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
        background: #EEEEEE
    }

    ::-webkit-scrollbar { 
        display: none; 
    }
</style>