<script setup>
import ThemeSwitcher from '@/components/ThemeSwitcher.vue'
import { useRouter } from 'vue-router'
import avatar from '@/assets/va.jpg'
import { ref, onMounted } from 'vue'

const router = useRouter()

// 技能数据
const skills = {
  frontend: [
    { name: 'JavaScript', icon: '📜' },
    { name: 'TypeScript', icon: '🔷' },
    { name: 'Vue', icon: '🟢' },
    { name: 'HTML5/CSS', icon: '🎨' },
    { name: 'Tailwind CSS', icon: '🌊' }
  ],
  backend: [
    { name: 'Java', icon: '☕' },
    { name: 'Spring Boot', icon: '🍃' },
    { name: 'Go', icon: '🐹' },
    { name: 'MyBatis', icon: '📊' },
    { name: 'Spring Cloud', icon: '☁️' }
  ],
  database: [
    { name: 'MySQL', icon: '🐬' },
    { name: 'Redis', icon: '🔴' },
    { name: 'Elasticsearch', icon: '🔍' },
    { name: 'MongoDB', icon: '🍃' }
  ],
  devops: [
    { name: 'Docker', icon: '🐳' },
    { name: 'Linux', icon: '🐧' },
    { name: 'Git', icon: '📋' },
    { name: 'Maven', icon: '🧩' }
  ]
}

// 主要项目
const projects = [
  {
    title: '智能之翼打卡平台',
    description: '为实验中心"智能之翼"实验室成员设计并开发的一站式管理平台。该平台整合了日常打卡、算法训练（在线编程、调试、通过率测试）、周报/文章发布与审阅、成员交流及动态值日表管理等多项功能。',
    tech: 'Spring Boot, Spring Security, Vue, MyBatis, MySQL, Redis',
    responsibilities: '主导整个项目的技术选型、系统架构设计与模块化规划。独立负责核心后端功能的开发与实现。设计并实现了一套后端服务，用于接收、编译和执行用户提交的算法代码，并实时反馈代码运行结果与通过率。',
    highlight: '荣获实验中心实验室项目评审二等奖，项目成功部署上线并在实验室内部投入实际应用。'
  },
  {
    title: 'AI职探',
    description: '面向职场新人与企业用户打造的智能化求职服务平台。通过集成大型语言模型（LLM），解决传统简历工具的痛点，提供个性化、智能化的简历生成与优化服务。平台亦支持简历在线投递、企业交流及模拟面试功能。',
    tech: 'Spring Boot, Vue, MyBatis, MySQL, Redis, Elasticsearch, WebSocket, JWT',
    responsibilities: '主导整个项目的技术架构设计、功能模块规划及前后端代码实现。采用WebSocket技术实现用户间即时消息传递和LLM交互的流式响应输出。集成Elasticsearch优化简历信息与招聘岗位的检索性能。',
    highlight: '荣获中国大学生计算机设计大赛国家级三等奖。'
  },
  {
    title: 'FlyinSSH',
    description: '为需要管理多台VPS的用户设计开发的Web端一体化管理工具。平台在浏览器端复现了常用SSH桌面客户端的核心功能，支持VPS连接管理、SFTP文件操作，以及通过内置代码编辑器在线修改服务器上的代码和配置文件。',
    tech: 'Spring Boot, Vue, MyBatis, MySQL, Redis, JSch, WebSocket, JWT',
    responsibilities: '主导项目架构设计与开发实现。设计基于WebSocket的通信方案，实现浏览器与服务器间的SSH隧道。利用JSch实现后端SSH/SFTP功能。创新设计Web端文件实时编辑与保存机制。',
    highlight: '成功实现网页端远程服务器管理的核心功能，提供便捷的多服务器Web管理方案。'
  },
  {
    title: '智论脉动',
    description: '面向高校师生的论文全周期智能辅助平台。通过构建"格式规范校验与智能调整、在线协同编辑与指导、模拟答辩预演、研究数据辅助建模"的闭环服务体系，解决传统论文写作中的核心痛点。',
    tech: 'Spring Boot, Vue, MyBatis, MySQL, Redis, WebSocket, JWT',
    responsibilities: '主导项目整体技术架构设计及核心功能开发。开发了高度可定制的在线论文编辑器，支持富文本编辑和拖拽式组件管理。实现了论文模板的创建、存储和复用机制。',
    highlight: '显著提升了论文写作和指导效率，为师生提供了一站式论文管理解决方案。'
  }
]

// 模拟博客文章数据（实际项目中可通过API获取）
const blogPosts = [
  {
    title: '​SpringBoot集成JWT令牌验证',
    date: '2024-09-24',
    summary: '​由于基于Seesion记忆客户端登陆状态，数据全部存储在...',
    url: 'https://blog.1024110.xyz/posts/springboot3/springboot%E9%9B%86%E6%88%90jwt%E4%BB%A4%E7%89%8C%E9%AA%8C%E8%AF%81'
  },
  {
    title: '新的RestfulAPI网络请求',
    date: '2023-11-16',
    summary: '之前写过一份Axios网络请求中有发布过一份前后端相互配合...',
    url: 'https://blog.1024110.xyz/posts/vue3withvite/newrestfulapi'
  },
  {
    title: '使用Nginx统一前后端域名',
    date: '2023-02-10',
    summary: '后端无疑是现流行的开发框架模式，出于网络安全，流行浏览...',
    url: 'http://blog.1024110.xyz/posts/%E4%BD%BF%E7%94%A8nginx%E7%BB%9F%E4%B8%80%E5%89%8D%E5%90%8E%E7%AB%AF%E5%9F%9F%E5%90%8D'
  }
]

// 动画控制
const isVisible = ref(false)
onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 300)
})
</script>

<template>
  <div class="min-h-screen bg-white dark:bg-gray-900 text-gray-800 dark:text-gray-200 transition-colors duration-300">
    <!-- 导航栏 -->
    <nav 
      v-motion
      :initial="{ opacity: 0, y: -50 }"
      :enter="{ opacity: 1, y: 0, transition: { delay: 100, duration: 500 } }"
      class="sticky top-0 z-50 bg-white dark:bg-[#0a0a16] shadow-sm border-b border-gray-200 dark:border-[#1a1a2e] backdrop-blur-sm dark:backdrop-blur-sm bg-opacity-80 dark:bg-opacity-80">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <div class="flex items-center">
            <span class="text-xl font-bold">龚靖文</span>
          </div>
          <div class="hidden sm:flex items-center gap-4">
            <a href="#about" class="hover:text-blue-600 dark:hover:text-blue-400">关于</a>
            <a href="#skills" class="hover:text-blue-600 dark:hover:text-blue-400">技能</a>
            <a href="#projects" class="hover:text-blue-600 dark:hover:text-blue-400">项目</a>
            <a href="#blog" class="hover:text-blue-600 dark:hover:text-blue-400">博客</a>
            <a href="#contact" class="hover:text-blue-600 dark:hover:text-blue-400">联系</a>
            <a href="/cv" class="flex items-center text-blue-600 dark:text-blue-400 font-medium">
              <span class="mr-1">📄</span> 查看简历
            </a>
            <ThemeSwitcher />
          </div>
        </div>
      </div>
    </nav>

    <!-- Mobile Nav Placeholder (Could be implemented with a burger menu) -->
    <div class="sm:hidden p-4 text-center sticky top-16 z-40 bg-white dark:bg-[#0a0a16] shadow-sm border-b border-gray-200 dark:border-[#1a1a2e]">
      <a href="/cv" class="text-blue-600 dark:text-blue-400 font-medium">📄 查看简历</a>
      <!-- Add more essential mobile links or a burger button here -->
    </div>

    <!-- 英雄区域 -->
    <section class="relative min-h-[80vh] flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-blue-100 to-purple-100 dark:from-[#0f0f25] dark:to-[#131339] opacity-50"></div>
      <div class="absolute inset-0 bg-[radial-gradient(circle_at_50%_50%,rgba(0,124,240,0.1),transparent_30%)] dark:bg-[radial-gradient(circle_at_50%_50%,rgba(138,58,185,0.15),transparent_40%)]"></div>
      
      <div 
        class="relative z-10 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center transition-all duration-700"
        :class="isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'"
      >
        <img 
          :src="avatar" 
          alt="龚靖文" 
          class="w-32 h-32 mx-auto mb-6 rounded-full object-cover border-4 border-white dark:border-[#1a1a2e] shadow-lg" 
          v-motion
          :initial="{ scale: 0.5, opacity: 0 }"
          :enter="{ scale: 1, opacity: 1, transition: { delay: 300, duration: 500 } }"
        />
        <h1 
          class="text-4xl sm:text-5xl font-bold mb-3 bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-purple-600 dark:from-[#8a3ab9] dark:to-[#4c68d7]"
          v-motion
          :initial="{ y: 50, opacity: 0 }"
          :enter="{ y: 0, opacity: 1, transition: { delay: 500, duration: 500 } }"
        >龚靖文</h1>
        <h2 
          class="text-xl sm:text-2xl mb-6 dark:text-gray-100"
          v-motion
          :initial="{ y: 50, opacity: 0 }"
          :enter="{ y: 0, opacity: 1, transition: { delay: 700, duration: 500 } }"
        >后端工程师 / 全栈开发者</h2>
        <p 
          class="text-base sm:text-lg max-w-2xl mx-auto mb-8 dark:text-gray-300"
          v-motion
          :initial="{ y: 50, opacity: 0 }"
          :enter="{ y: 0, opacity: 1, transition: { delay: 900, duration: 500 } }"
        >专注于JavaScript/TypeScript生态与Java开发，擅长前后端开发、架构设计与云原生技术，热衷于用技术解决实际问题。</p>
        <div 
          class="flex justify-center gap-4"
          v-motion
          :initial="{ y: 50, opacity: 0 }"
          :enter="{ y: 0, opacity: 1, transition: { delay: 1100, duration: 500 } }"
        >
          <a 
            href="/cv" 
            class="px-6 py-3 bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 dark:from-[#8a3ab9] dark:to-[#4c68d7] dark:hover:from-[#7a309f] dark:hover:to-[#3c58c7] text-white font-medium rounded-md shadow-md hover:shadow-lg transition-all duration-300"
          >
            查看简历
          </a>
          <a 
            href="#contact" 
            class="px-6 py-3 bg-white dark:bg-[#1a1a2e] text-blue-600 dark:text-[#8a3ab9] font-medium rounded-md shadow-md hover:shadow-lg transition-all duration-300"
          >
            联系我
          </a>
        </div>
      </div>
    </section>

    <!-- 关于我 -->
    <section id="about" class="py-12 sm:py-16 bg-gradient-to-b from-gray-50 to-gray-100 dark:from-[#0a0a16] dark:to-[#0f0f25]">
      <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 
          class="text-2xl sm:text-3xl font-bold mb-8 text-center bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-blue-800 dark:from-blue-400 dark:to-blue-600"
          v-motion-slide-visible-top
          :delay="200"
        >关于我</h2>
        <div class="text-base sm:text-lg space-y-4 bg-white dark:bg-[#1a1a2e] rounded-xl shadow-lg p-6" v-motion-fade-visible :delay="400">
          <p>我是一名热爱技术的软件工程师，对构建高性能、可扩展的应用系统充满热情。专注于后端开发，擅长运用Java和Golang生态工具解决实际问题。</p>
          <p>在技术领域，我喜欢探索新技术，对代码质量和最佳实践有着较高的追求。目前正在深入研究分布式系统和微服务架构，同时也在不断提升前端开发能力。</p>
          <p>作为学院实验中心智能之翼实验室负责人，我负责实验室日常管理和维护工作，同时也带领团队参与各类项目和竞赛，并在小学期综合实践中担任项目组长，获得"优秀项目"奖。</p>
          <p class="mt-4 font-medium">🏆 竞赛成果：</p>
          <ul class="list-disc pl-6 space-y-1 text-sm sm:text-base">
            <li>第十七届全国大学生计算机设计大赛国家级三等奖</li>
            <li>第十七届全国大学生计算机设计大赛安徽省级赛一等奖</li>
            <li>第十五届蓝桥杯大赛软件赛B组安徽省级三等奖</li>
            <li>第十四届蓝桥杯大赛软件赛B组安徽省级三等奖</li>
          </ul>
          <div class="flex flex-wrap gap-3 justify-center mt-6">
            <span class="bg-blue-100 dark:bg-blue-900/40 rounded-full px-3 py-1 text-sm sm:text-base sm:px-4 flex items-center">
              <span class="mr-1">📍</span>浙江宁波 / 杭州
            </span>
            <span class="bg-blue-100 dark:bg-blue-900/40 rounded-full px-3 py-1 text-sm sm:text-base sm:px-4 flex items-center">
              <span class="mr-1">🎓</span>安徽信息工程学院 (2022-2026)
            </span>
          </div>
        </div>
      </div>
    </section>

    <!-- 技能展示 -->
    <section id="skills" class="py-12 sm:py-16 dark:bg-[#0a0a16] bg-white">
      <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 
          class="text-2xl sm:text-3xl font-bold mb-8 text-center bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-blue-800 dark:from-blue-400 dark:to-blue-600"
          v-motion-slide-visible-top
          :delay="200"
        >专业技能</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <!-- 前端技能 -->
          <div 
            class="bg-gradient-to-br from-white to-gray-50 dark:from-[#1a1a2e] dark:to-[#1f1f3d] rounded-xl shadow-lg overflow-hidden transition-all hover:shadow-xl border border-gray-100 dark:border-gray-800"
            v-motion-fade-visible
            :delay="300"
          >
            <div class="bg-gradient-to-r from-blue-600 to-blue-700 dark:from-[#4c68d7] dark:to-[#3c58c7] text-white p-4 flex items-center">
              <span class="text-xl mr-2">🎨</span>
              <h3 class="text-lg sm:text-xl font-semibold">前端开发</h3>
            </div>
            <div class="p-5">
              <div class="flex flex-wrap gap-2 sm:gap-3">
                <div v-for="(skill, i) in skills.frontend" :key="skill.name" 
                  v-motion
                  :initial="{ opacity: 0, y: 20 }"
                  :visible="{ opacity: 1, y: 0, transition: { delay: 400 + i * 50 } }"
                  class="flex items-center px-3 py-2 bg-gray-100 dark:bg-[#292957] rounded-full transition-transform hover:scale-105 text-sm sm:text-base hover:bg-blue-50 dark:hover:bg-[#353580] shadow-sm">
                  <span class="mr-2 text-lg">{{ skill.icon }}</span>
                  {{ skill.name }}
                </div>
              </div>
              <div class="mt-4 text-sm text-gray-600 dark:text-gray-400">
                <p>• 熟悉掌握HTML, CSS, JavaScript基础</p>
                <p>• 熟练使用Vue.js框架及相关生态工具</p>
                <p>• 熟悉前后端分离架构与Restful接口设计</p>
                <p>• 熟悉AntDesign, Tailwindcss等UI框架</p>
              </div>
            </div>
          </div>
          
          <!-- 后端技能 -->
          <div 
            class="bg-gradient-to-br from-white to-gray-50 dark:from-[#1a1a2e] dark:to-[#1f1f3d] rounded-xl shadow-lg overflow-hidden transition-all hover:shadow-xl border border-gray-100 dark:border-gray-800"
            v-motion-fade-visible
            :delay="400"
          >
            <div class="bg-gradient-to-r from-green-600 to-green-700 dark:from-[#5c68d7] dark:to-[#4c58c7] text-white p-4 flex items-center">
              <span class="text-xl mr-2">☕</span>
              <h3 class="text-lg sm:text-xl font-semibold">后端开发</h3>
            </div>
            <div class="p-5">
              <div class="flex flex-wrap gap-2 sm:gap-3">
                <div v-for="(skill, i) in skills.backend" :key="skill.name" 
                  v-motion
                  :initial="{ opacity: 0, y: 20 }"
                  :visible="{ opacity: 1, y: 0, transition: { delay: 500 + i * 50 } }"
                  class="flex items-center px-3 py-2 bg-gray-100 dark:bg-[#292957] rounded-full transition-transform hover:scale-105 text-sm sm:text-base hover:bg-green-50 dark:hover:bg-[#353580] shadow-sm">
                  <span class="mr-2 text-lg">{{ skill.icon }}</span>
                  {{ skill.name }}
                </div>
              </div>
              <div class="mt-4 text-sm text-gray-600 dark:text-gray-400">
                <p>• 熟悉Java语言，具备JVM调优和问题排查能力</p>
                <p>• 熟练使用Spring全家桶相关框架</p>
                <p>• 熟悉Go语言开发，掌握gin, gorm等框架</p>
                <p>• 熟悉分布式系统设计与微服务架构</p>
              </div>
            </div>
          </div>
          
          <!-- 数据库 -->
          <div 
            class="bg-gradient-to-br from-white to-gray-50 dark:from-[#1a1a2e] dark:to-[#1f1f3d] rounded-xl shadow-lg overflow-hidden transition-all hover:shadow-xl border border-gray-100 dark:border-gray-800"
            v-motion-fade-visible
            :delay="500"
          >
            <div class="bg-gradient-to-r from-purple-600 to-purple-700 dark:from-[#8a3ab9] dark:to-[#7a309f] text-white p-4 flex items-center">
              <span class="text-xl mr-2">🔍</span>
              <h3 class="text-lg sm:text-xl font-semibold">数据库 & 中间件</h3>
            </div>
            <div class="p-5">
              <div class="flex flex-wrap gap-2 sm:gap-3">
                <div v-for="(skill, i) in skills.database" :key="skill.name" 
                  v-motion
                  :initial="{ opacity: 0, y: 20 }"
                  :visible="{ opacity: 1, y: 0, transition: { delay: 600 + i * 50 } }"
                  class="flex items-center px-3 py-2 bg-gray-100 dark:bg-[#292957] rounded-full transition-transform hover:scale-105 text-sm sm:text-base hover:bg-purple-50 dark:hover:bg-[#353580] shadow-sm">
                  <span class="mr-2 text-lg">{{ skill.icon }}</span>
                  {{ skill.name }}
                </div>
              </div>
              <div class="mt-4 text-sm text-gray-600 dark:text-gray-400">
                <p>• 熟练掌握MySQL数据库及性能优化</p>
                <p>• 熟悉Redis缓存设计与应用场景</p>
                <p>• 了解Elasticsearch搜索引擎的配置与使用</p>
                <p>• 熟悉常见数据库优化方案与设计模式</p>
              </div>
            </div>
          </div>
          
          <!-- DevOps -->
          <div 
            class="bg-gradient-to-br from-white to-gray-50 dark:from-[#1a1a2e] dark:to-[#1f1f3d] rounded-xl shadow-lg overflow-hidden transition-all hover:shadow-xl border border-gray-100 dark:border-gray-800"
            v-motion-fade-visible
            :delay="600"
          >
            <div class="bg-gradient-to-r from-orange-600 to-orange-700 dark:from-[#ad5389] dark:to-[#9d4379] text-white p-4 flex items-center">
              <span class="text-xl mr-2">🐧</span>
              <h3 class="text-lg sm:text-xl font-semibold">DevOps & 运维</h3>
            </div>
            <div class="p-5">
              <div class="flex flex-wrap gap-2 sm:gap-3">
                <div v-for="(skill, i) in skills.devops" :key="skill.name" 
                  v-motion
                  :initial="{ opacity: 0, y: 20 }"
                  :visible="{ opacity: 1, y: 0, transition: { delay: 700 + i * 50 } }"
                  class="flex items-center px-3 py-2 bg-gray-100 dark:bg-[#292957] rounded-full transition-transform hover:scale-105 text-sm sm:text-base hover:bg-orange-50 dark:hover:bg-[#353580] shadow-sm">
                  <span class="mr-2 text-lg">{{ skill.icon }}</span>
                  {{ skill.name }}
                </div>
              </div>
              <div class="mt-4 text-sm text-gray-600 dark:text-gray-400">
                <p>• 熟悉Linux系统操作与服务器管理</p>
                <p>• 掌握Docker容器化部署技术</p>
                <p>• 熟悉CI/CD持续集成与部署流程</p>
                <p>• 熟悉网站部署上线、域名解析与SSL证书配置</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 项目经验 -->
    <section id="projects" class="py-12 sm:py-16 bg-gradient-to-b from-gray-50 to-gray-100 dark:from-[#0f0f25] dark:to-[#0a0a16]">
      <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 
          class="text-2xl sm:text-3xl font-bold mb-8 text-center bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-blue-800 dark:from-blue-400 dark:to-blue-600"
          v-motion-slide-visible-top
          :delay="200"
        >项目经验</h2>
        
        <div class="space-y-8">
          <div v-for="(project, index) in projects" :key="index"
            class="bg-white dark:bg-[#1a1a2e] rounded-xl shadow-lg overflow-hidden transition-all hover:shadow-xl border border-gray-100 dark:border-gray-800"
            v-motion-fade-visible
            :delay="300 + index * 150"
          >
            <div class="p-5 sm:p-6">
              <h3 class="text-lg sm:text-xl font-bold mb-3 text-blue-700 dark:text-blue-400">{{ project.title }}</h3>
              <p class="mb-4 dark:text-gray-300 text-sm sm:text-base">{{ project.description }}</p>
              
              <div class="mb-4 flex flex-wrap gap-2">
                <span v-for="(tech, i) in project.tech.split(', ')" :key="i"
                  class="px-2 py-1 bg-blue-50 dark:bg-blue-900/20 text-blue-700 dark:text-blue-300 rounded-md text-xs"
                >{{ tech }}</span>
              </div>
              
              <div class="mb-3">
                <p class="text-sm text-gray-700 dark:text-gray-300"><span class="font-medium text-gray-900 dark:text-gray-100">个人职责:</span> {{ project.responsibilities }}</p>
              </div>
              
              <div class="pt-3 border-t border-gray-100 dark:border-gray-800">
                <p class="text-blue-600 dark:text-[#ad5389] text-sm sm:text-base flex items-center">
                  <span class="mr-2">✨</span> {{ project.highlight }}
                </p>
              </div>
            </div>
          </div>
        </div>
        
        <div 
          class="text-center mt-10"
          v-motion-fade-visible
          :delay="300 + projects.length * 150"
        >
          <a 
            href="/cv" 
            class="inline-flex items-center px-6 py-3 bg-blue-600 hover:bg-blue-700 dark:bg-gradient-to-r dark:from-[#4c68d7] dark:to-[#8a3ab9] text-white font-medium rounded-lg shadow-md hover:shadow-lg transition-all duration-300"
          >
            查看完整简历
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2" viewBox="0 0 20 20" fill="currentColor">
              <path fill-rule="evenodd" d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
            </svg>
          </a>
        </div>
      </div>
    </section>

    <!-- 最新博客 -->
    <section id="blog" class="py-12 sm:py-16 dark:bg-[#0a0a16]">
      <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 
          class="text-2xl sm:text-3xl font-bold mb-8 text-center"
          v-motion-slide-visible-top
          :delay="200"
        >技术分享</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <a v-for="(post, index) in blogPosts" :key="post.title" :href="post.url" target="_blank"
            class="bg-white dark:bg-[#1a1a2e] rounded-lg shadow-md overflow-hidden transition-all hover:shadow-lg hover:-translate-y-1"
            v-motion-fade-visible
            :delay="300 + index * 150"
          >
            <div class="p-5 sm:p-6">
              <h3 class="text-base sm:text-lg font-bold mb-2 dark:text-gray-100">{{ post.title }}</h3>
              <p class="text-xs sm:text-sm text-gray-500 dark:text-gray-400 mb-3">{{ post.date }}</p>
              <p class="text-sm sm:text-base dark:text-gray-300">{{ post.summary }}</p>
            </div>
          </a>
        </div>
        
        <div 
          class="text-center mt-10"
          v-motion-fade-visible
          :delay="300 + blogPosts.length * 150"
        >
          <a 
            href="https://blog.1024110.xyz" 
            target="_blank"
            class="inline-flex items-center text-blue-600 dark:text-[#8a3ab9] hover:underline font-medium"
          >
            查看所有文章
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
              <path fill-rule="evenodd" d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
            </svg>
          </a>
        </div>
      </div>
    </section>

    <!-- 联系方式 -->
    <section id="contact" class="py-12 sm:py-16 bg-gradient-to-b from-gray-50 to-gray-100 dark:from-[#0a0a16] dark:to-[#0f0f25]">
      <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 
          class="text-2xl sm:text-3xl font-bold mb-8 text-center bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-blue-800 dark:from-blue-400 dark:to-blue-600"
          v-motion-slide-visible-top
          :delay="200"
        >保持联系</h2>
        <div 
          class="bg-white dark:bg-[#1a1a2e] rounded-xl shadow-lg overflow-hidden p-6 md:p-8 border border-gray-100 dark:border-gray-800"
          v-motion-fade-visible
          :delay="400"
        >
          <p class="text-base sm:text-lg mb-6 dark:text-gray-300">对我的经历感兴趣？有合作机会？或者只是想聊聊技术？欢迎通过以下方式联系我。</p>
          
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
            <div class="flex flex-col gap-4">
              <a href="mailto:w2084151024@gmail.com" class="flex items-center text-base sm:text-lg hover:text-blue-600 dark:hover:text-blue-400 transition-colors duration-300">
                <span class="text-2xl mr-3 bg-blue-100 dark:bg-blue-900/40 p-2 rounded-full flex items-center justify-center w-10 h-10">📧</span>
                <div>
                  <p class="font-medium">电子邮件</p>
                  <p class="text-sm text-gray-600 dark:text-gray-400">1509743314@qq.com</p>
                </div>
              </a>
              <a href="tel:18058289662" class="flex items-center text-base sm:text-lg hover:text-blue-600 dark:hover:text-blue-400 transition-colors duration-300">
                <span class="text-2xl mr-3 bg-blue-100 dark:bg-blue-900/40 p-2 rounded-full flex items-center justify-center w-10 h-10">📱</span>
                <div>
                  <p class="font-medium">电话</p>
                  <p class="text-sm text-gray-600 dark:text-gray-400">19858802724</p>
                </div>
              </a>
            </div>
            <div class="flex flex-col gap-4">
              <a href="https://blog.1024110.xyz" target="_blank" class="flex items-center text-base sm:text-lg hover:text-blue-600 dark:hover:text-blue-400 transition-colors duration-300">
                <span class="text-2xl mr-3 bg-blue-100 dark:bg-blue-900/40 p-2 rounded-full flex items-center justify-center w-10 h-10">📝</span>
                <div>
                  <p class="font-medium">博客</p>
                  <p class="text-sm text-gray-600 dark:text-gray-400">blog.1024110.xyz</p>
                </div>
              </a>
              <a href="https://github.com/Flyinsky2004" target="_blank" class="flex items-center text-base sm:text-lg hover:text-blue-600 dark:hover:text-blue-400 transition-colors duration-300">
                <span class="text-2xl mr-3 bg-blue-100 dark:bg-blue-900/40 p-2 rounded-full flex items-center justify-center w-10 h-10">🐙</span>
                <div>
                  <p class="font-medium">GitHub</p>
                  <p class="text-sm text-gray-600 dark:text-gray-400">github.com/19xiaxi</p>
                </div>
              </a>
            </div>
          </div>
          
          <div class="text-center">
            <a 
              href="/cv" 
              class="inline-flex items-center px-6 py-3 bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 dark:from-[#4c68d7] dark:to-[#8a3ab9] text-white font-medium rounded-lg shadow-md hover:shadow-lg transition-all duration-300"
              v-motion
              :initial="{ scale: 0.8, opacity: 0 }"
              :visible="{ scale: 1, opacity: 1, transition: { delay: 800 } }"
            >
              <span class="mr-2">📄</span> 查看完整简历
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- 页脚 -->
    <footer 
      class="py-8 border-t border-gray-200 dark:border-[#1a1a2e] bg-white dark:bg-[#0a0a16]"
      v-motion-fade-visible
      :delay="200"
    >
      <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-sm text-gray-500 dark:text-gray-400">
        <p>© {{ new Date().getFullYear() }} 龚靖文. 保留所有权利.</p>
        <p class="mt-2">使用 Vue 3 + Tailwind CSS 构建</p>
        <div class="flex justify-center gap-4 mt-4">
          <a href="https://github.com/Flyinsky2004" target="_blank" class="hover:text-gray-700 dark:hover:text-blue-400 transition-colors">GitHub</a>
          <a href="https://blog.1024110.xyz" target="_blank" class="hover:text-gray-700 dark:hover:text-blue-400 transition-colors">博客</a>
          <a href="/cv" class="hover:text-gray-700 dark:hover:text-blue-400 transition-colors">简历</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* 可选的额外样式 */
</style>