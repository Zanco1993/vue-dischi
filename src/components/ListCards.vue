<template>
    <div class="box-card">
        <img :src="innerCard.poster" alt="">
        <h3>{{ innerCard.title.toUpperCase() }}</h3>
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