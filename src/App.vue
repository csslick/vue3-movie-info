<template>
  <Navbar />
  <Event />
  <Search :data="data" />

  <section class="container">
    <h1>영화정보</h1>
    <Movies 
      :data="data" 
      @openModal="isModal=true; selectedMovie=$event"
      @handleLike="increaseLike($event)"
    />
  </section>

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
      searchMovieName: 'name', 
    }
  },
  methods: {
    increaseLike(i) {
      this.data[i].like += 1;
    }
  },
  components: {
    Navbar: AppNavbar,
    Modal: Modal,
    Movies: Movies,
    Search: Search,
    Event: Event,
  }
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
 </style>

