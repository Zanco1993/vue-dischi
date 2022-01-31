<template>
    <div class="container-cards">
        <list-cards
        v-for="(card, index) in dischi"
        :key="index"
        :innerCard="card" />
        <list-cards />
    </div>
</template>

<script>
import ListCards from './ListCards.vue'
export default {
    components: {
        ListCards

    },

    props: {
        dischi: Array,
    }
}
</script>

<style lang="scss" scoped>
    .container-cards {
        margin-top: 100px;
        width: 1200px;
        border: 1px solid black;
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
}
</style>