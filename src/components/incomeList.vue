<template>
    <div class="income-list">
        <incomeItems v-for="items in assest1.sortItems" :key="items.id" :income="items" @remove-item="removeItem" />
    </div>
</template>

<script>
import incomeItems from "./incomeItems.vue";

export default {
    components: {
        incomeItems
    },
    props: {
        assest1: Object
    },
    setup(props, { emit }) {

        function removeItem(id) {
            emit("remove-item", id);
        };

        return {
            removeItem
        }
    }
}
</script>