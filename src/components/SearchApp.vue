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
      <span>Seleziona Artista: </span>
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
    <div class="content-reset">
      <button @click="$emit('reset')" class="reset">Reset</button>
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

  .content-reset {
    text-align: center;
    
    .reset {
      border-radius: 10px;
      padding: 10px 20px;
      margin-left: 50px;
      transition: all 0.3s;

      &:hover {
        background-color: red;
      }
    }
  }
</style>