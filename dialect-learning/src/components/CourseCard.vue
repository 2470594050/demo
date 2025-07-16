<template>
  <div class="course-card">
    <div class="course-image">
      <img :src="getImageUrl(image)" alt="Course" />
    </div>
    <div class="course-content">
      <h3>{{ title }}</h3>
      <p class="course-description">{{ description }}</p>
      <div class="course-info">
        <span class="course-level">{{ level }}</span>
        <span class="course-duration">{{ duration }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CourseCard',
  props: {
    image: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    level: {
      type: String,
      default: '入门'
    },
    duration: {
      type: String,
      default: '30分钟'
    }
  },
  methods: {
    getImageUrl(name) {
      return new URL(`../assets/images/${name}`, import.meta.url).href
    }
  }
}
</script>

<style scoped>
.course-card {
  background-image: v-bind('`url(${getImageUrl("FRAME-extra.png")})`');
  background-size: cover;
  border-radius: 12px;
  overflow: hidden;
  height: 100%;
  display: flex;
  flex-direction: column;
  transition: transform 0.3s;
}

.course-card:hover {
  transform: translateY(-5px);
}

.course-image {
  height: 160px;
  overflow: hidden;
}

.course-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.course-content {
  padding: 15px;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.course-content h3 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #333;
}

.course-description {
  font-size: 14px;
  color: #666;
  margin-bottom: 15px;
  flex-grow: 1;
}

.course-info {
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  color: #999;
}

.course-level {
  background-color: #f0f7ff;
  color: #1890ff;
  padding: 2px 8px;
  border-radius: 10px;
}

.course-duration {
  color: #999;
}
</style> 