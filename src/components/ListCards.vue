<template>
    <div class="box-card">
        <img :src="innerCard.poster" alt="">
        <h2>{{ innerCard.title.toUpperCase() }}</h2>
        <p>{{ innerCard.author }}</p>
        <p>{{ innerCard.year }}</p>
    </div>
</template>

<script>
export default {
    props: {
        innerCard: Object
    }
}
</script>

<style lang="scss" scoped>
@import './style/card.scss';
</style>