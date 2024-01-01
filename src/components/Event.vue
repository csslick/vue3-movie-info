<template>
  <div class="event" :class="{ show: isEvent }">
    <!-- <p>NETPLIX 강렬한 운명의 드라마, 경기크리처</p> -->
    <p>{{ text }}</p>
    <button @click="isEvent = false">X</button>
  </div>
</template>

<script>
export default {
  name: 'EventBox',
  data() {
    return {
      isEvent: true,
    }
  },
  props: {
    text: Object,
  }
}
</script>

<style>
.event {
  width: 100%;
  background: #333;
  padding: 5px 1em;
  display: flex;
  justify-content: center;
  gap: 30px;
  align-items: center;
  color: #fff;
  text-align: center;
  margin-bottom: 1em;
  
  max-height: 0;
  opacity: 0;
  overflow: hidden;
  transition: all 0.4s;
}

.show {
  opacity: 1;
  max-height: 100px;
}
</style>