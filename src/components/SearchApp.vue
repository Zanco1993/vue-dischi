<template>
  <div>
    <div class="content-input">
      <span>Seleziona il genere: </span>
      <select @change="$emit('searchGenre', input)" v-model="input">
        <option disabled value="">Seleziona Genere</option>
        <option value="All">All</option>
        <option value="Rock">Rock</option>
        <option value="Pop">Pop</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
      </select>
    </div>
    <div class="content-input">
      <span>Seleziona Album: </span>
      <select @change="$emit('searchArtist', input)" v-model="input">
        <option disabled value="">Seleziona Artista</option>
        <option value="All">All</option>
        <option v-for="(autore, index) in dischi" 
        :key="index" 
        :value="autore.author"
        >
        {{ autore.author }}
        </option>
      </select>
    </div>


  </div>
  
</template>

<script>
export default {
  data() {
    return {
      input: ''
    };
  },
  props: {
    dischi: Array
  }
};
</script>

<style lang="scss" scoped>
.content-input {
  text-align: center;
  padding: 20px;

  span {
    color: white;
    font-size: 20px;
  }
  div {
    color: white;
    font-size: 20px;
  }
}
</style>