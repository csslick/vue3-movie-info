<template lang="">
  <div class="search-box">
    <!-- 검색어 입력 완료 후  -->
    <input 
      type="search" 
      @change="
        inputText = $event.target.value; 
        $event.target.value = ''
      "
    >
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
    },
    props: {
      data: Object,
    },
    // 입력한 영화제목이 데이터에 있는지 확인
    watch: {
      inputText(name) {
        const findName = this.data.find(item => {
          return item.title === name;
        })

        if(!findName) alert('해당하는 정보가 없습니다')
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