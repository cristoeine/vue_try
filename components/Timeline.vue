<template>
    <div class="timeline-container">
      <ul class="timeline">
        <li v-for="(item, index) in timelineItems" :key="index" :class="getItemClasses(index).li">
          <div :class="getItemClasses(index).dot">
            <div class="card">
              <h3>{{ item.year }}</h3>
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
      dot: isEven ? 'dotLeft' : 'dotRight'
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
  background-color: white;
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -3px;
}

.card {
  padding: 20px;
  background-color: #e5e9f3;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  max-width: 400px;
  margin: 0 auto;
}

.left, .right {
  position: relative;
  width: 50%;
  padding: 10px 40px;
  box-sizing: border-box;
}

.left {
  left: 0;
}

.right {
  left: 50%;
}

.dotLeft::before, .dotRight::before {
  content: "";
  position: absolute;
  width: 25px;
  height: 25px;
  background-color: white;
  border: 4px solid #559cff;
  top: 15px;
  border-radius: 50%;
  z-index: 1;
}

.dotLeft::before {
  right: -17px;
}

.dotRight::before {
  left: -17px;
}

@media screen and (max-width: 600px) {
  .timeline::after {
    left: 31px;
  }
  
  .left, .right {
    width: 100%;
    padding-left: 70px;
    padding-right: 25px;
  }
  
  .right {
    left: 0%;
  }
  
  .dotLeft::before, .dotRight::before {
    left: 15px;
  }
}
</style>