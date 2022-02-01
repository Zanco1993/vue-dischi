<template>
    <div class="content-input">
        <span>Seleziona il genere: </span>
        <select @click="$emit('search', select)" v-model="select">
        
            <option value="All">All</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>      
        </select>
        <span>{{ select }}</span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            select: ''
        }
    }
}
</script>

<style lang="scss" scoped>
    .content-input {
        text-align: center;
        padding: 50px;

        span {
            color: white;
            font-size: 20px;
        }
    }
</style>