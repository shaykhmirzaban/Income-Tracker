<template>
  <div class="incomeItems">
    <div class="remove-Items" @click="removeItem">X</div>
    <div class="description">{{income.desc}}</div>
    <div class="value">${{income.value}}</div>
    <div class="date">{{formateDate}}</div>
  </div>
</template>

<script>
export default {
    props: {
        income: Object
    },
    provide() {
        return {
            message: "Welcome"
        }
    },
    setup (props, { emit }) {

        let date = new Date(props.income.date);
        let day = date.getDate();
        let month = date.getMonth();
        let year = date.getFullYear();

        let formateDate = `${day}/${month}/${year}`;

        function removeItem () {
            emit("remove-item", props.income.id);
        }

        return {
            formateDate,
            removeItem
        }
    }
}
</script>