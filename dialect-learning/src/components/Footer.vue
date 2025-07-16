<template>
  <footer class="footer">
    <div class="container footer-container">
      <div class="footer-1"></div>
      <div class="footer-content">
        <div class="footer-section">
          <h3>关于我们</h3>
          <ul>
            <li><a href="#">公司介绍</a></li>
            <li><a href="#">联系我们</a></li>
            <li><a href="#">加入我们</a></li>
          </ul>
        </div>

        <div class="footer-section">
          <h3>帮助中心</h3>
          <ul>
            <li><a href="#">使用指南</a></li>
            <li><a href="#">常见问题</a></li>
            <li><a href="#">意见反馈</a></li>
          </ul>
        </div>

        <div class="footer-section">
          <h3>帮助中心</h3>
          <ul>
            <li><a href="#">使用指南</a></li>
            <li><a href="#">常见问题</a></li>
            <li><a href="#">意见反馈</a></li>
          </ul>
        </div>
        <div class="footer-right">
          <h3 style="margin-left: 15px">关于我们</h3>
          <div class="footer-icons">
            <a href="#" class="footer-icon">
              <img :src="getImageUrl('image-20250714223325522.png')" alt="Icon 1" />
            </a>
            <a href="#" class="footer-icon">
              <img :src="getImageUrl('image-20250714223403610.png')" alt="Icon 2" />
            </a>
          </div>
        </div>
      </div>
      <div class="footer-divider"></div>
      <div class="footer-bottom">
        <p>© 2025 方言通. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  methods: {
    getImageUrl(name) {
      return new URL(`../assets/images/${name}`, import.meta.url).href
    }
  }
}
</script>

<style scoped>
.footer {
  background-image: v-bind('`url(${getImageUrl("image-20250714223146535.png")})`');
  background-size: cover;
  padding-left: 0;
  margin-top: 60px;
}

.footer-container {
  display: flex;
  flex-direction: column;
}

.footer-1 {
  height: 1px;
  margin-bottom: 30px;
}


.footer-divider {
  height: 1px;
  background-image: v-bind('`url(${getImageUrl("image-20250714223224861.png")})`');
  background-size: contain;
  margin-bottom: 15px;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  margin-bottom: 30px;
}

.footer-section {
  flex: 1;
}
.footer-section a {
  color: rgb(139,126,116);
}
.footer-right{
  flex: 2;
}
.footer-right h3 {
  font-size: 15px;
  margin-bottom: 15px;
  font-weight: 400;
  color: rgb( 95,113, 97);
}
.footer-section h3 {
  font-size: 15px;
  margin-bottom: 15px;
  font-weight: 400;
  color: rgb( 95,113, 97);
}

.footer-section p, .footer-section li {
  font-size: 15px;
  margin-bottom: 8px;
  color: rgb(139,126,116);
}

.footer-icons {
  margin-left: 30px;
}
.footer-icon{
  margin-right: 10px;
}

.footer-icon img {
  width: 24px;
  height: 24px;
}

.footer-bottom {
  text-align: center;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding: 15px 0;
  font-size: 15px;
  color: rgb(139,126,116);
}

.footer-bottom p {
  margin: 0;
  font-weight: 400;
}
</style> 