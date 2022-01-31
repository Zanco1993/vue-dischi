<template>
    <div class="container-cards">
        <list-cards
        v-for="(card, index) in dischi"
        :key="index"
        :innerCard="card" />
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
        margin: 100px auto;
        display: flex;
        flex-wrap: wrap;
}
</style>