<template>
    <div class="header">
        <h1>
            <span class="uniqueStyle">i</span>ncome
            -
            <span class="uniqueStyle">t</span>racker
        </h1>
        <button type="button" class="total-income">
            ${{ totalIncome }}
        </button>
    </div>
</template>

<script>
export default {
    props: {
        totalIncome: Number
    }
}
</script>