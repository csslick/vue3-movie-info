<template lang="">
  <div v-for="(movie) in data" :key="movie.id" class="item">
    <figure>
      <!-- 동적으로 이미지 경로를 설정합니다. -->
      <img :src="require(`../assets/images/${movie.imgUrl}`)" alt="">
    </figure>
    <div class="info">
      <h3>{{ movie.title }}</h3>
      <p>개봉: {{ movie.year }}</p>
      <p>장르: {{ movie.category }}</p>
      <button @click="$emit('handleLike', movie.id)">좋아요</button> <span>{{ movie.like }}</span>
      <p>
        <button @click="$emit('openModal', movie.id)">상세보기</button>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MoviesUI',
  props: {
    data: Object,
  },
  emits: ['handleLike', 'openModal'], // 발생시키는 이벤트를 선언합니다.
}
</script>

<style lang="">
  
</style>