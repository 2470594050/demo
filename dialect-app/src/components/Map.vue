<template>
  <div class="map-container">
    <!-- 分类部分 -->
    <div class="categories-section">
      <!-- 方言类型 -->
      <div class="dialect-types">
        <div class="category-background">
          <img src="/frame-5.png" alt="分类背景" class="background-image" />
          <div class="dialect-list">
            <div v-for="dialect in dialectTypes" :key="dialect.name" class="dialect-item">
              <span class="dialect-name">{{ dialect.name }}</span>
              <span class="dialect-count">{{ dialect.count }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- 文化主题 -->
      <div class="cultural-themes">
        <div class="theme-grid">
          <div v-for="theme in culturalThemes" :key="theme.name" class="theme-item">
            <img :src="theme.icon" :alt="theme.name" class="theme-icon" />
            <span class="theme-name">{{ theme.name }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- 地图部分 -->
    <div class="map-section">
      <img src="/map.png" alt="地图" class="map-image" />
    </div>

    <!-- 播放语音示例 -->
    <div class="audio-section">
      <div class="audio-example">
        <button class="play-button" @click="togglePlay">
          <img src="/play-button.png" alt="播放" class="play-icon" />
        </button>
        <span class="audio-label">播放语音示例</span>
      </div>

      <!-- 播放进度条 -->
      <div class="progress-section">
        <button class="control-button" @click="previousTrack">
          <img src="/container3.png" alt="上一首" class="control-icon" />
        </button>
        
        <div class="progress-bar">
          <div class="progress-track">
            <div 
              class="progress-fill" 
              :style="{ width: progressPercent + '%' }"
            ></div>
          </div>
          <span class="time-display">{{ currentTime }} / {{ totalTime }}</span>
        </div>
        
        <button class="control-button" @click="nextTrack">
          <img src="/container2.png" alt="下一首" class="control-icon" />
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

// 方言类型数据
const dialectTypes = reactive([
  { name: '官话方言', count: 12 },
  { name: '吴方言', count: 8 },
  { name: '闽方言', count: 6 },
  { name: '粤方言', count: 7 },
  { name: '客家方言', count: 5 },
  { name: '湘方言', count: 4 },
  { name: '赣方言', count: 5 }
])

// 文化主题数据
const culturalThemes = reactive([
  { name: '民间故事', icon: '/h80.png' },
  { name: '地方戏曲', icon: '/h84.png' },
  { name: '民俗节日', icon: '/h89.png' },
  { name: '地方小吃', icon: '/h93.png' },
  { name: '传统工艺', icon: '/h97.png' }
])

// 音频控制状态
const isPlaying = ref(false)
const progressPercent = ref(35) // 示例进度
const currentTime = ref('01:23')
const totalTime = ref('03:45')

// 播放控制方法
const togglePlay = () => {
  isPlaying.value = !isPlaying.value
  // 这里可以添加实际的音频播放逻辑
}

const previousTrack = () => {
  // 上一首音频逻辑
  console.log('Previous track')
}

const nextTrack = () => {
  // 下一首音频逻辑
  console.log('Next track')
}
</script>

<style scoped>
.map-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

/* 分类部分样式 */
.categories-section {
  display: flex;
  gap: 30px;
  margin-bottom: 30px;
}

.dialect-types {
  flex: 1;
}

.category-background {
  position: relative;
  display: inline-block;
}

.background-image {
  width: 100%;
  height: auto;
}

.dialect-list {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.dialect-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 15px;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 15px;
  min-width: 120px;
}

.dialect-name {
  font-size: 14px;
  color: #333;
}

.dialect-count {
  font-size: 14px;
  font-weight: bold;
  color: #007bff;
}

.cultural-themes {
  flex: 1;
}

.theme-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  gap: 15px;
}

.theme-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  cursor: pointer;
  transition: transform 0.2s;
}

.theme-item:hover {
  transform: scale(1.05);
}

.theme-icon {
  width: 40px;
  height: 40px;
  margin-bottom: 8px;
}

.theme-name {
  font-size: 12px;
  color: #666;
}

/* 地图部分样式 */
.map-section {
  text-align: center;
  margin-bottom: 30px;
}

.map-image {
  max-width: 100%;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* 音频部分样式 */
.audio-section {
  background: #f8f9fa;
  border-radius: 15px;
  padding: 20px;
}

.audio-example {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 20px;
}

.play-button {
  background: none;
  border: none;
  cursor: pointer;
  transition: transform 0.2s;
}

.play-button:hover {
  transform: scale(1.1);
}

.play-icon {
  width: 50px;
  height: 50px;
}

.audio-label {
  font-size: 16px;
  color: #333;
  font-weight: 500;
}

/* 进度条部分样式 */
.progress-section {
  display: flex;
  align-items: center;
  gap: 15px;
}

.control-button {
  background: none;
  border: none;
  cursor: pointer;
  transition: transform 0.2s;
}

.control-button:hover {
  transform: scale(1.1);
}

.control-icon {
  width: 30px;
  height: 30px;
}

.progress-bar {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.progress-track {
  width: 100%;
  height: 6px;
  background: #e0e0e0;
  border-radius: 3px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #007bff, #0056b3);
  transition: width 0.3s ease;
}

.time-display {
  font-size: 12px;
  color: #666;
  text-align: center;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .categories-section {
    flex-direction: column;
    gap: 20px;
  }
  
  .theme-grid {
    grid-template-columns: repeat(3, 1fr);
  }
  
  .progress-section {
    flex-wrap: wrap;
    gap: 10px;
  }
  
  .progress-bar {
    order: 3;
    width: 100%;
  }
}
</style>