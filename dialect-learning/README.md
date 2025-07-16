# 方言学习平台

基于 Vue 3 开发的方言学习平台前端项目。

## 项目特点

- 基于 Vue 3 + Vite 构建
- 使用 Vue Router 进行路由管理
- 响应式设计，适配多种设备尺寸
- 模块化组件设计

## 项目结构

```
dialect-learning/
├── public/
├── src/
│   ├── assets/
│   │   └── images/        # 图片资源
│   ├── components/        # 公共组件
│   │   ├── NavBar.vue     # 导航栏组件
│   │   ├── Footer.vue     # 页脚组件
│   │   ├── CourseCard.vue # 课程卡片组件
│   │   └── ChallengeCard.vue # 挑战卡片组件
│   ├── router/            # 路由配置
│   │   └── index.js
│   ├── views/             # 页面视图
│   │   ├── Home.vue       # 首页
│   │   ├── Map.vue        # 地图页
│   │   ├── Learn.vue      # 学习页
│   │   ├── Community.vue  # 社区页
│   │   └── Profile.vue    # 个人中心页
│   ├── App.vue            # 根组件
│   └── main.js            # 入口文件
├── package.json
└── vite.config.js
```

## 功能模块

- **首页**：展示热门学习课程和正在进行的方言挑战
- **地图**：方言地图功能（开发中）
- **学习**：方言学习课程（开发中）
- **社区**：用户交流社区（开发中）
- **个人中心**：用户个人信息（开发中）

## 开发指南

### 安装依赖

```bash
npm install
```

### 开发环境运行

```bash
npm run dev
```

### 构建生产版本

```bash
npm run build
```

## 后续开发计划

- 完善地图、学习、社区和个人中心页面
- 对接后端 API，实现数据交互
- 添加用户认证功能
- 优化移动端体验
