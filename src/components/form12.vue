<template>
  <form @submit.prevent="getData()">
    <input type="text" placeholder="Description..." v-model="data.desc" class="focus">
    <input type="number" placeholder="Value..." v-model="data.amount">
    <input type="date" placeholder="Date..." v-model="data.date">
    <input type="submit" placeholder="Submit">
  </form>
</template>

<script>
import {reactive} from "vue";

export default {
    props: {
        assest: Object
    },
    setup (props, { emit }) {
        
        let data = reactive({
            desc : null,
            amount : null,
            date : null
        });

        function getData () {
            
            if(data.desc !== null && data.amount !== null && data.date !== null) {
                emit("get-data", {
                desc : data.desc,
                amount : data.amount,
                date : data.date
                })
            } 
            else{
                alert("Please fill all input field.");
            }

            data.desc = null;
            data.amount = null;
            data.date = null;

            let des = document.querySelector('.focus');
            des.focus(); 
        };

        return {
            data,
            getData
        }
    }
}
</script>