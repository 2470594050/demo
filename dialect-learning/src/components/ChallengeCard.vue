<template>
  <div class="challenge-card">
    <div class="challenge-header">
      <h3>{{ title }}</h3>
    </div>
    <div class="challenge-content">
      <div class="challenge-stats">
        <div class="stat">
          <img  :src="getImageUrl('image-20250714222832434.png')" alt="Participants" />
          <span>{{ participants }}人参与</span>
        </div>
        <div class="stat">
          <img :src="getImageUrl('image-20250714222851518.png')" alt="Likes" />
          <span>{{ likes }}人点赞</span>
        </div>
        <div class="stat">
          <img :src="getImageUrl('image-20250714222905781.png')" alt="Comments" />
          <span>{{ comments }}条评论</span>
        </div>
      </div>
    </div>
    <div class="challenge-footer">
      <button class="challenge-button"></button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ChallengeCard',
  props: {
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    region: {
      type: String,
      required: true
    },
    level: {
      type: String,
      default: '入门'
    },
    participants: {
      type: Number,
      default: 0
    },
    likes: {
      type: Number,
      default: 0
    },
    comments: {
      type: Number,
      default: 0
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
.challenge-card {
  background-image: v-bind('`url(${getImageUrl("FRAME3.png")})`');
  background-size: cover;
  border-radius: 12px;
  padding: 20px;
  height: 280px;
  width: 508px;
  display: flex;
  flex-direction: column;
}

.challenge-header {
  margin-bottom: 15px;
  text-align: left; /* 内容靠左 */
}

.challenge-header h3 {
  font-size: 18px;
  margin-bottom: 10px;
  font-weight: 500;
  padding-left: 45px; /*离左边25px */
  color: rgb( 95,113, 97);
}

.challenge-tags {
  display: flex;
  gap: 10px;
}

.challenge-tag {
  background-color: rgba(255, 255, 255, 0.2);

  padding: 2px 8px;
  border-radius: 10px;
  font-size: 12px;
}

.challenge-content {
  flex-grow: 1;
  margin-bottom: 20px;
}

.challenge-content p {

  font-size: 14px;
  margin-bottom: 20px;
}

.challenge-stats {
  display: flex;
  flex-direction: column; /* 竖向排列 */
  align-items: flex-start; /* 所有子元素靠左对齐 */
  padding-left: 45px; /* 整体左缩进 */
  gap: 10px; /* 可选：上下间距更均匀 */
}

.stat {
  display: flex;
  align-items: center;
  font-size: 15px;
  padding-bottom: 12px;
}

.stat img {
  width: 25px;
  height: 25px;
  margin-right: 8px;
}
.stat span {
  color: rgb(139,126,116);
}

.challenge-footer {
  text-align: center;
}

.challenge-button {
  background-image: v-bind('`url(${getImageUrl("FRAME-extraText1.png")})`');
  background-size:  100% auto; /* 宽度放大到 120%，高度自动等比放大 */
  background-repeat: no-repeat; /* ✅ 不重复背景图 */
  width: 380px;
  height: 36px;
  border: none;
  cursor: pointer;
  background-color: transparent;
  transition: opacity 0.3s;
  outline: none; /* 取消默认焦点轮廓 */
}

.challenge-button:hover {
  opacity: 0.9;
}
</style> 