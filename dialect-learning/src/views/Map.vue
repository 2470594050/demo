<template>
  <div class="map-page">
    <!-- 导航栏直接放在页面中 -->
    <nav class="navbar">
      <div class="navbar-container">
        <div class="navbar-brand">
          <img :src="getImageUrl('蒙版分组.png')" alt="Logo" class="logo" />
          <img :src="getImageUrl('labels (1).png')" alt="Label" class="label" />
        </div>
        
        <div class="navbar-menu">
          <router-link to="/" class="navbar-item" :class="{ 'active': $route.name === 'Home' }">
            <div class="navbar-item-icon">
              <img :src="$route.name === 'Home' ? getImageUrl('蒙版分组 (1).png') : getImageUrl('Group 7.png')" alt="Home" />
            </div>
            <span class="navbar-item-text">首页</span>
          </router-link>
          
          <router-link to="/map" class="navbar-item" :class="{ 'active': $route.name === 'Map' }">
            <div class="navbar-item-icon">
              <img :src="$route.name === 'Map' ? getImageUrl('Group 6 (1).png') : getImageUrl('蒙版分组 (2).png')" alt="Map" />
            </div>
            <span class="navbar-item-text">地图</span>
          </router-link>
          
          <router-link to="/learn" class="navbar-item" :class="{ 'active': $route.name === 'Learn' }">
            <div class="navbar-item-icon">
              <img :src="$route.name === 'Learn' ? getImageUrl('Group 10.png') : getImageUrl('蒙版分组 (3).png')" alt="Learn" />
            </div>
            <span class="navbar-item-text">学习</span>
          </router-link>
          
          <router-link to="/community" class="navbar-item" :class="{ 'active': $route.name === 'Community' }">
            <div class="navbar-item-icon">
              <img :src="$route.name === 'Community' ? getImageUrl('Group 12.png') : getImageUrl('分组 1.png')" alt="Community" />
            </div>
            <span class="navbar-item-text">社区</span>
          </router-link>
          
          <router-link to="/profile" class="navbar-item" :class="{ 'active': $route.name === 'Profile' }">
            <div class="navbar-item-icon">
              <img :src="$route.name === 'Profile' ? getImageUrl('蒙版分组 (4).png') : getImageUrl('蒙版分组 (4).png')" alt="Profile" />
            </div>
            <span class="navbar-item-text">我的</span>
          </router-link>
        </div>
        
        <div class="navbar-search">
          <div class="search-box">
            <img :src="getImageUrl('Subtract.png')" alt="Search" class="search-icon" />
            <input type="text" placeholder="搜索" />
          </div>
        </div>
      </div>
    </nav>
    
    <!-- 分隔线 -->
    <div class="divider"></div>

    <!-- 主要内容区域 -->
    <div class="main-content">
      <!-- 分类部分 -->
      <div class="categories-section">
        <!-- 方言类型分类 -->
        <div class="dialect-categories">
          <div class="category-background">
            <img :src="getImageUrl('FRAME (5).png')" alt="分类背景" class="category-bg-image" />
            <div class="dialect-types">
              <div
                v-for="(dialect, index) in dialectTypes"
                :key="index"
                class="dialect-type-item"
                :class="{ 'active': selectedDialect === dialect.name }"
                @click="selectDialect(dialect.name)"
              >
                <span class="dialect-name">{{ dialect.name }}</span>
                <span class="dialect-count">{{ dialect.count }}</span>
              </div>
            </div>
          </div>
        </div>

        <!-- 文化主题 -->
        <div class="culture-themes">
          <div
            v-for="(theme, index) in cultureThemes"
            :key="index"
            class="theme-item"
            @click="selectTheme(theme.name)"
          >
            <img :src="getImageUrl(theme.icon)" :alt="theme.name" class="theme-icon" />
            <span class="theme-name">{{ theme.name }}</span>
          </div>
        </div>
      </div>

      <!-- 地图部分 -->
      <div class="map-section">
        <div class="map-container">
          <img :src="getImageUrl('image4.png')" alt="方言地图" class="map-image" />
        </div>
      </div>

      <!-- 播放语音示例部分 -->
      <div class="audio-section">
        <div class="audio-example">
          <h3 class="audio-title">播放语音示例</h3>
          <div class="audio-controls">
            <button class="play-button" @click="togglePlay">
              <img :src="getImageUrl('image-20250716170627237.png')" alt="播放按钮" class="play-icon" />
            </button>
          </div>
        </div>

        <!-- 播放进度条 -->
        <div class="progress-section">
          <div class="progress-controls">
            <button class="control-button" @click="previousTrack">
              <img :src="getImageUrl('容器3.png')" alt="上一首" class="control-icon" />
            </button>

            <div class="progress-bar-container">
              <div class="progress-bar">
                <div class="progress-fill" :style="{ width: progressPercent + '%' }"></div>
                <div class="progress-handle" :style="{ left: progressPercent + '%' }"></div>
              </div>
              <div class="time-display">
                <span class="current-time">{{ formatTime(currentTime) }}</span>
                <span class="total-time">{{ formatTime(totalTime) }}</span>
              </div>
            </div>

            <button class="control-button" @click="nextTrack">
              <img :src="getImageUrl('容器2.png')" alt="下一首" class="control-icon" />
            </button>
          </div>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Footer from '../components/Footer.vue'

export default {
  name: 'Map',
  components: {
    Footer
  },
  methods: {
    getImageUrl(name) {
      return new URL(`../assets/images/${name}`, import.meta.url).href
    }
  }
}
</script>

<style scoped>
.map-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  padding-top: 0; /* 移除顶部填充 */
  width: 100%;
}

.container {
  flex: 1;
  padding: 40px 15px;
  text-align: center;
  max-width: 1400px;
  margin: 0 auto;
  width: 100%;
}

h1 {
  margin-bottom: 20px;
}

/* 导航栏样式 */
.navbar {
  background-color: transparent;
  background-image: v-bind('`url(${getImageUrl("index-back.png")})`');
  background-size: cover;
  background-position: center;
  padding: 15px 0;
  width: 100%;
}

.navbar::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(255, 255, 255, 0.9);
  z-index: -1;
}

.navbar-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  padding: 0 20px;
  max-width: 1400px;
  margin: 0 auto;
}

.navbar-brand {
  display: flex;
  align-items: center;
}

.logo {
  height: 40px;
  margin-right: 10px;
}

.label {
  height: 24px;
}

.navbar-menu {
  display: flex;
  gap: 30px;
}

.navbar-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  color: #999;
  font-size: 14px;
  transition: color 0.3s;
  text-decoration: none;
}

.navbar-item-icon {
  margin-right: 8px;
}

.navbar-item img {
  height: 16px;
}

.navbar-item-text {
  font-weight: 500;
}

.navbar-item.active {
  color: rgb(192,108, 82);
}

.navbar-search {
  position: relative;
}

.search-box {
  display: flex;
  align-items: center;
  background: url('../assets/images/FRAME (1).png') no-repeat;
  background-size: contain;
  width: 200px;
  height: 36px;
  padding: 0 15px;
}

.search-icon {
  width: 16px;
  height: 16px;
  margin-right: 8px;
}

.search-box input {
  background: transparent;
  border: none;
  outline: none;
  width: 100%;
  font-size: 14px;
  color: #333;
}

.search-box input::placeholder {
  color: #999;
}

/* 分隔线样式 */
.divider {
  height: 1px;
  background-color: #e0e0e0;
  width: 100%;
  margin: 0 auto;
}
</style> 