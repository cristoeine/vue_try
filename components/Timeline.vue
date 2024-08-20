<template>
  <div class="timeline-container">
    <ul class="timeline">
      <li v-for="(item, index) in timelineItems" :key="index" :class="getItemClasses(index).li">
        <div :class="getItemClasses(index).dot">
          <div class="year-box">
            <h3>{{ item.year }}</h3>
          </div>
          <div class="event-description">
            <p>{{ item.event }}</p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { defineProps, computed } from 'vue'

const props = defineProps({
  timelineItems: {
    type: Array,
    required: true
  }
})

const getItemClasses = (index) => {
  const isEven = index % 2 === 0
  return {
    li: isEven ? 'left' : 'right',
    dot: isEven ? 'lineLeft' : 'lineRight'
  }
}
</script>

<style scoped>
.timeline-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.timeline {
  position: relative;
  padding: 0;
  list-style: none;
}

.timeline::after {
  content: "";
  position: absolute;
  width: 6px;
  background-color: #136ae5;
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -3px;
}

.year-box {
  background-color: #fff;
  border: 3px solid #136ae5;
  border-radius: 20px;
  padding: 5px 25px;
  display: inline-block;
  margin-bottom: 10px;
}

.event-description {
  background-color: #f5f5f5;
  padding: 15px;
  border-radius: 8px;
  max-width: 400px;
}

.left, .right {
  position: relative;
  width: 50%;
  padding: 10px 40px;
  box-sizing: border-box;
}

.left {
  left: 0;
  text-align: right;
}

.right {
  left: 50%;
  text-align: left;
}

.lineLeft::before, .lineRight::before {
  content: "";
  position: absolute;
  width: 48px;
  height: 4px;
  background-color: #136ae5;
  top: 40px;
  border-radius: 10%;
  z-index: 1;
}

.lineLeft::before {
  right: -4px;
}

.lineRight::before {
  left: -4px;
}

@media screen and (max-width: 600px) {
  .timeline::after {
    left: 31px;
  }
  
  .left, .right {
    width: 100%;
    padding-left: 70px;
    padding-right: 25px;
    text-align: left;
    margin-top: 16px;
  }
  
  .right {
    left: 0%;
  }
  
  .lineLeft::before, .lineRight::before {
    left: 28px;
    width: 45px;
  }
}
</style>