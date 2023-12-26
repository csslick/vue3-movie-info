<template lang="">
  <div class="search-box">
    <input type="search" @input="inputText = $event.target.value"/>
    <button>검색</button>
  </div>
  <p style="text-align:center">{{ inputText }}</p>
</template>
<script>
export default {
  name: "SearchBar",
  data() {
    return {
      inputText: '',
    }
  }
  
}
</script>
<style>
  .search-box {
    padding: 10px;
    display: flex;
    justify-content: center;
    text-align: center;
  }

  .search-box input {
    padding: 5px 10px;
  }

</style>