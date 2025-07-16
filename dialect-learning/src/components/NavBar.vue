<template>
  <nav class="navbar">
    <div class="container navbar-container">
      <div class="navbar-brand">
        <img :src="getImageUrl('蒙版分组.png')" alt="Logo" class="logo" />
        <img :src="getImageUrl('labels (1).png')" alt="Label" class="label" />
      </div>
      
      <div class="navbar-menu">
        <router-link to="/" class="navbar-item" :class="{ 'active': isActive('Home') }">
          <div class="navbar-item-icon">
            <img :src="isActive('Home') ? getImageUrl('蒙版分组 (1).png') : getImageUrl('Group 7.png')" alt="Home" />
          </div>
          <span class="navbar-item-text">首页</span>
        </router-link>
        
        <router-link to="/map" class="navbar-item" :class="{ 'active': isActive('Map') }">
          <div class="navbar-item-icon">
            <img :src="isActive('Map') ? getImageUrl('Group 6 (1).png') : getImageUrl('蒙版分组 (2).png')" alt="Map" />
          </div>
          <span class="navbar-item-text">地图</span>
        </router-link>
        
        <router-link to="/learn" class="navbar-item" :class="{ 'active': isActive('Learn') }">
          <div class="navbar-item-icon">
            <img :src="isActive('Learn') ? getImageUrl('Group 10.png') : getImageUrl('蒙版分组 (3).png')" alt="Learn" />
          </div>
          <span class="navbar-item-text">学习</span>
        </router-link>
        
        <router-link to="/community" class="navbar-item" :class="{ 'active': isActive('Community') }">
          <div class="navbar-item-icon">
            <img :src="isActive('Community') ? getImageUrl('Group 12.png') : getImageUrl('分组 1.png')" alt="Community" />
          </div>
          <span class="navbar-item-text">社区</span>
        </router-link>
        
        <router-link to="/profile" class="navbar-item" :class="{ 'active': isActive('Profile') }">
          <div class="navbar-item-icon">
            <img :src="isActive('Profile') ? getImageUrl('蒙版分组 (4).png') : getImageUrl('蒙版分组 (4).png')" alt="Profile" />
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
</template>

<script>
import { computed } from 'vue'
import { useRoute } from 'vue-router'

export default {
  name: 'NavBar',
  setup() {
    const route = useRoute()
    
    const isActive = (name) => {
      return computed(() => route.name === name).value
    }
    
    const getImageUrl = (name) => {
      return new URL(`../assets/images/${name}`, import.meta.url).href
    }
    
    return {
      isActive,
      getImageUrl
    }
  }
}
</script>

<style scoped>
.navbar {
  background-color: transparent;
  background-image: v-bind('`url(${getImageUrl("index-back.png")})`');
  background-size: cover;
  background-position: center;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  padding: 15px 0;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
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
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 20px;
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
</style> 