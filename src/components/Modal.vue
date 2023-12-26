<template lang="">
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{ data[selectedMovie].title }}</h3>
      <p>영화 상세정보</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MovieModal',
  props: {
    data: Object,
    isModal: Boolean,
    selectedMovie: Number
  }
}
</script>

<style lang="">
  
</style>