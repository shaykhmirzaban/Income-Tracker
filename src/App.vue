<template>
  <header12 :totalIncome="assest.totalIncome" />
  <form12 @get-data="getUserData" :bydefaultValue="updateItem" />
  <incomeList :assest1="assest" @remove-item="removeItem" />
</template>

<script>
import { reactive, computed } from "vue";

import header12 from "./components/Header12.vue";
import form12 from "./components/form12.vue";
import incomeList from "./components/incomeList.vue";

export default {
  components: {
    header12,
    form12,
    incomeList
  },
  setup() {
    const assest = reactive({
      income: [],

      totalIncome: computed(() => {
        let temp = 0;

        if (assest.income.length > 0) {
          for (let i = 0; i < assest.income.length; i++) {
            temp += assest.income[i].value;
          }
        }

        return temp;
      }),

      sortItems: computed(() => {
        let asdf = assest.income.sort((a, b) => { return b.id - a.id });
        return asdf;
      })

    });

    function getUserData(data) {

      let d = data.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);

      assest.income = [...assest.income, {
        id: Date.now(),
        desc: data.desc,
        value: data.amount,
        date: newD.getTime()
      }];
      
    };

    function removeItem(id) {
      assest.income = assest.income.filter(a => { return a.id != id });
    };

    return {
      assest,
      getUserData,
      removeItem
    }
  }
}
</script>