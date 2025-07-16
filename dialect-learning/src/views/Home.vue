<template>
  <div class="home">
    <div class="background-image"></div>
    <div class="content-wrapper">
      <!-- 导航栏直接放在页面中 -->
      <nav class="navbar">
        <div class="navbar-container">
          <div class="navbar-brand">
            <img :src="getImageUrl('蒙版分组.png')" alt="Logo" class="logo"/>
            <img :src="getImageUrl('labels (1).png')" alt="Label" class="label"/>
          </div>

          <div class="navbar-menu">
            <router-link to="/" class="navbar-item" :class="{ 'active': $route.name === 'Home' }">
              <div class="navbar-item-icon">
                <img :src="$route.name === 'Home' ? getImageUrl('蒙版分组 (1).png') : getImageUrl('Group 7.png')"
                     alt="Home"/>
              </div>
              <span class="navbar-item-text">首页</span>
            </router-link>

            <router-link to="/map" class="navbar-item" :class="{ 'active': $route.name === 'Map' }">
              <div class="navbar-item-icon">
                <img :src="$route.name === 'Map' ? getImageUrl('Group 6 (1).png') : getImageUrl('蒙版分组 (2).png')"
                     alt="Map"/>
              </div>
              <span class="navbar-item-text">地图</span>
            </router-link>

            <router-link to="/learn" class="navbar-item" :class="{ 'active': $route.name === 'Learn' }">
              <div class="navbar-item-icon">
                <img :src="$route.name === 'Learn' ? getImageUrl('Group 10.png') : getImageUrl('蒙版分组 (3).png')"
                     alt="Learn"/>
              </div>
              <span class="navbar-item-text">学习</span>
            </router-link>

            <router-link to="/community" class="navbar-item" :class="{ 'active': $route.name === 'Community' }">
              <div class="navbar-item-icon">
                <img :src="$route.name === 'Community' ? getImageUrl('Group 12.png') : getImageUrl('分组 1.png')"
                     alt="Community"/>
              </div>
              <span class="navbar-item-text">社区</span>
            </router-link>

            <router-link to="/profile" class="navbar-item" :class="{ 'active': $route.name === 'Profile' }">
              <div class="navbar-item-icon">
                <img
                    :src="$route.name === 'Profile' ? getImageUrl('蒙版分组 (4).png') : getImageUrl('蒙版分组 (4).png')"
                    alt="Profile"/>
              </div>
              <span class="navbar-item-text">我的</span>
            </router-link>
          </div>

          <div class="navbar-search">
            <div class="search-box">
              <input style="height: 45px" type="text" placeholder="搜索方言、课程、活动"/>
              <button class="search-button">
                <img :src="getImageUrl('Subtract.png')" alt="Search" class="search-icon"/>
              </button>
            </div>
          </div>
        </div>
      </nav>

      <!-- 分隔线 -->
      <div class="divider"></div>

      <div class="main-content">
        <div class="context">
          <!-- Top Sections -->
          <div class="top-sections">
            <div class="left-section">
              <img :src="getImageUrl('FRAME.png')" alt="Left Frame" class="frame-image"/>
            </div>

            <div class="right-section">
              <img :src="getImageUrl('FRAME (2).png')" alt="Right Frame" class="frame-image"/>
              <button class="center-button">
                <img style="width: 90px" :src="getImageUrl('FRAME-extraText.png')" alt="Button"/>
              </button>
            </div>
          </div>

          <div>
            <div class="center-section">
              <img :src="getImageUrl('Frame 3.png')" alt="Center Frame" class="frame-image"/>
            </div>
          </div>

          <!-- Popular Courses Section -->
          <section class="courses-section">
            <h2 class="section-title">热门学习课程</h2>
            <div class="courses-grid">
              <CourseCard
                  v-for="(course, index) in popularCourses"
                  :key="index"
                  :image="course.image"
                  :title="course.title"
                  :description="course.description"
                  :level="course.level"
                  :duration="course.duration"
              />
            </div>
          </section>

          <!-- Dialect Challenges Section -->
          <section class="challenges-section">
            <h2 class="section-title">正在进行的方言挑战</h2>
            <div class="challenges-grid">
              <ChallengeCard
                  v-for="(challenge, index) in dialectChallenges"
                  :key="index"
                  :title="challenge.title"
                  :description="challenge.description"
                  :region="challenge.region"
                  :level="challenge.level"
                  :participants="challenge.participants"
                  :likes="challenge.likes"
                  :comments="challenge.comments"
              />
            </div>
          </section>

        </div>
        <div>
          <Footer/>
        </div>
      </div>


    </div>
  </div>
</template>

<script>
import Footer from '../components/Footer.vue'
import CourseCard from '../components/CourseCard.vue'
import ChallengeCard from '../components/ChallengeCard.vue'

export default {
  name: 'Home',
  components: {
    Footer,
    CourseCard,
    ChallengeCard
  },
  data() {
    return {
      popularCourses: [
        {
          image: 'image.png',
          title: '粤语基础入门',
          description: '学习广东话的基本发音和日常用语',
          level: '入门',
          duration: '30分钟'
        },
        {
          image: 'image (1).png',
          title: '四川话速成',
          description: '掌握四川方言的特色词汇和表达方式',
          level: '中级',
          duration: '45分钟'
        },
        {
          image: 'image (2).png',
          title: '上海话实用会话',
          description: '学习上海方言的日常交流和特色表达',
          level: '入门',
          duration: '40分钟'
        },
        {
          image: 'image (3).png',
          title: '东北话趣味学习',
          description: '了解东北方言的幽默表达和文化背景',
          level: '高级',
          duration: '60分钟'
        }
      ],
      dialectChallenges: [
        {
          title: '粤语歌曲挑战',
          description: '挑战自己用粤语演唱经典粤语歌曲，展示你的粤语发音能力',
          region: '广东',
          level: '中级',
          participants: 1256,
          likes: 876,
          comments: 324
        },
        {
          title: '四川话绕口令',
          description: '尝试用地道的四川话说出经典绕口令，考验你的方言掌握程度',
          region: '四川',
          level: '高级',
          participants: 986,
          likes: 752,
          comments: 198
        },
        {
          title: '东北话情景对话',
          description: '参与东北方言的情景对话挑战，感受地道的东北文化',
          region: '东北',
          level: '入门',
          participants: 1542,
          likes: 1024,
          comments: 456
        }
      ]
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
.home {
  position: relative;
  min-height: 100vh;
  width: 1690px; /* 宽度铺满整个屏幕 */
  padding: 0 0 0 0; /* 移除顶部填充 */
  z-index: 1;

}

.background-image {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: v-bind('`url(${getImageUrl("index-back.png")})`');
  background-size: cover;
  background-position: center;
  background-attachment: scroll;
  z-index: 0;
}

.content-wrapper {
  position: relative;
  z-index: 1;
  width: 100%; /* 铺满整个屏幕 */
  box-sizing: border-box;
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
  max-width: 1600px;
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
  color: rgb(192, 108, 82);
}

.navbar-search {
  position: relative;
}

.search-box {
  display: flex;
  align-items: center;
  background: url('../assets/images/FRAME (1).png') no-repeat;
  background-size: 120% auto; /* 宽度放大到 120%，高度自动等比放大 */
  width: 250px;
  height: 45px;
  margin-top: 5px;
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
  height: 100%;
  font-size: 14px;
  padding-bottom: 5px;
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

.main-content {
  position: absolute;
  width: 100%;
  max-width: 1700px;
  min-height: calc(100vh - 80px - 300px);
  transform: translateX(-50%);
  margin: 0 auto;
  padding-top: 20px;
  left: 50%;
  z-index: 1;
}

.context {
  max-width: 1600px;
  margin: 0 auto;
}

.top-sections {
  display: flex;
  gap: 20px;
  margin-bottom: 40px;
  padding: 0 0 0 10px;
}

.left-section, .center-section, .right-section {
  flex: 1;
  position: relative;
  padding: 0 20px;
}

.frame-image {
  width: 100%;
  border-radius: 12px;
}

.right-section {
  display: flex;
  justify-content: center;
  align-items: center;
}

.center-button {
  margin-top: 50px;
  position: absolute;
  background: none;
  border: none;
  cursor: pointer;
  transition: transform 0.3s;
  outline: none; /* 取消默认焦点轮廓 */
}

.center-button:hover {
  transform: scale(1.05);
}

.search-button {
  background: none;
  border: none;
  cursor: pointer;
  transition: transform 0.3s;
  padding-right: 0;
  outline: none; /* 取消默认焦点轮廓 */
}

.search-button:hover {
  transform: scale(1.05);
}

.section-title {
  font-size: 18px;
  font-weight: 400;
  margin-top: 30px;
  margin-bottom: 30px;
  color: #333;
  position: relative;
  text-align: left; /* 强制文字靠左 */
}

.section-title::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 5px;
  height: 20px;

  border-radius: 2px;
}

.courses-section, .challenges-section {
  margin-bottom: 40px;
  padding: 0 20px;
  border-radius: 10px;
}

.courses-grid, .challenges-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

@media (max-width: 1200px) {
  .courses-grid, .challenges-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 992px) {
  .courses-grid, .challenges-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .top-sections {
    flex-direction: column;
  }
}

@media (max-width: 576px) {
  .courses-grid, .challenges-grid {
    grid-template-columns: 1fr;
  }
}
</style>