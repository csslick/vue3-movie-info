<template lang="">
  <form class="search-box">
    <!-- 검색어 입력 완료 후  -->
    <input 
      type="search" 
      @change="
        $emit('searchMovie', $event.target.value)
        inputText = $event.target.value;
        $event.target.value = '';
      "
    >
    <button>검색</button>
  </form>
  <p style="text-align:center">{{ inputText }}</p>
</template>
<script>
  export default {
    name: "SearchBar",
    data() {
      return {
        inputText: '',
      }
    },
    props: {
      data: Object,
    },
    // 입력한 영화제목이 데이터에 있는지 확인
    watch: {
      inputText(name) {
        const findName = this.data.filter(movie => {
          return movie.title.includes(name);
        })
        if(findName.length == 0) alert('해당하는 정보가 없습니다')
      }
    },
    emits: ['searchMovie']  // 이벤트 명시
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