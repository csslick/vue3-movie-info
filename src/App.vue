<template>
  <Navbar />
  <Event :text="eventText[eventTextNum]" />
  <div :style="{textAlign: 'center'}">
    <Search 
      :data="data_temp" 
      @searchMovie="searchMovie($event)"
    />
    <p >
      <button @click="showAllMovie" class="btn-all">전체보기</button>
    </p>
  </div>

  <main class="container">
    <h1>영화정보</h1>
    <Movies 
      :data="data_temp" 
      @openModal="isModal=true; selectedMovie=$event"
      @handleLike="increaseLike($event)"
    />
  </main>

  <transition name="fade">
    <Modal 
      @closeModal="isModal=false"
      :data="data" 
      :isModal="isModal" 
      :selectedMovie="selectedMovie"
    />
  </transition>

</template>

<script>
import movie from './assets/movie';
import AppNavbar from './components/Navbar.vue';
import Modal from './components/Modal.vue';
import Movies from './components/Movies.vue';
import Search from './components/Search.vue';
import Event from './components/Event.vue';

export default {
  name: 'App',
  data() {
    return {
      selectedMovie: 0,
      isModal: false,
      data: movie,
      data_temp: movie,
      searchMovieName: 'name',
      eventText: [
        'NETPLIX 강렬한 운명의 드라마, 경기크리처',
        '디즈니 100주년 기념작, 위시',
        '그날, 대한민국의 운명이 바뀌었다, 서울의 봄'
      ],
      eventTextNum: 0,
    }
  },
  methods: {
    increaseLike(i) {
      this.data[i].like += 1;
    },
    searchMovie(title) {
      // 영화제목이 포함된 자료를 반환
      this.data_temp = this.data.filter(movie => {
        return movie.title.includes(title);
      })
      console.log('title: ', title)
      console.log('검색된 데이터: ', this.data_temp)
    },
    showAllMovie() {
      this.data_temp = [...this.data];
    }

  },
  components: {
    Navbar: AppNavbar,
    Modal: Modal,
    Movies: Movies,
    Search: Search,
    Event: Event,
  },
  mounted() {
    console.log('mounted');
    setTimeout(() => {
      this.eventTextNum += 1;
    }, 3000)
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
}

.container {
  padding: 20px;
}

.item {
  border: 1px solid #ccc;
  margin-bottom: 10px;
  padding: 20px;
  display: flex;
  gap: 30px;
}

figure {
  width: 30%;
  margin: 0;
}

figure img {
  width: 100%;
}

.modal {
  background: rgba(0, 0, 0, 0.7);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}

/* 트랜지션 시작 상태 */
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

.btn-all {

}
 </style>

