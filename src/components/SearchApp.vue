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
        <option value="Bon Jovi">Bon Jovi</option>
        <option value="Queen">Queen</option>
        <option value="Sting">Sting</option>
        <option value="Steve Gadd Band">Steve Gadd Band</option>
        <option value="Iron Maiden">Iron Maiden</option>
        <option value="Eric Clapton">Eric Clapton</option>
        <option value="Deep Purple">Deep Purple</option>
        <option value="Metallica">Metallica</option>
        <option value="Dave Weckl">Dave Weckl</option>
        <option value="Michael Jacjson">Michael Jacjson</option>
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