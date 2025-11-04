<script setup>
import ThemeSwitcher from '@/components/ThemeSwitcher.vue'
import html2pdf from 'html2pdf.js'
import avatar from '@/assets/avatar.pic.jpg'
const downloadPDF = () => {
    const element = document.getElementById('resume-content')
    const opt = {
        margin: 0,
        filename: '龚靖文的简历.pdf',
        image: { type: 'jpeg', quality: 0.98 },
        html2canvas: { scale: 2 },
        jsPDF: { unit: 'in', format: 'a4', orientation: 'portrait' }
    }
    html2pdf().set(opt).from(element).save()
}
</script>
<template>
    <div class="bg-white dark:bg-black min-h-screen p-4">
        <div class="flex justify-between mb-3">
            <button 
                @click="downloadPDF"
                class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded flex items-center"
            >
                <span class="mr-2">📥</span> 下载简历
            </button>
            <ThemeSwitcher/>
        </div>
        
        <div id="resume-content" class="max-w-4xl mx-auto bg-white dark:bg-gray-950 shadow-lg overflow-hidden">
            <!-- 头部信息 -->
            <div class="px-6 py-3 bg-blue-600 dark:bg-blue-800 text-white">
                <div class="flex items-start gap-4">
                    <!-- 头像 -->
                    <img :src="avatar" alt="头像" class="w-28 object-cover border-2 border-white"/>
                    
                    <!-- 个人信息 -->
                    <div class="flex-1">
                        <div class="flex justify-between items-center mb-2">
                            <div>
                                <h1 class="text-2xl font-bold">龚靖文</h1>
                                <p class="text-sm mt-1">2004-08</p>
                            </div>
                            <p class="text-lg">期望职位：Java后端/数据分析与挖掘工程师</p>
                        </div>
                        <div class="grid grid-cols-2 text-sm gap-y-1">
                            <p>📍 籍贯：湖南邵阳</p>
                            <p>📱 19858802724</p>
                            <p>📧 1509743314@qq.com</p>
                            <p>🔗 <a href="https://blog.09091024.xyz" class="hover:underline" target="_blank">博客：blog.09091024.xyz</a></p>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- 主体内容 -->
            <div class="px-6 py-3 text-gray-800 dark:text-gray-200">
                <div class="grid grid-cols-2 gap-4">
                    <!-- 左侧栏 -->
                    <div>
                        <!-- 教育经历 -->
                        <div class="mb-4">
                            <h2 class="text-lg font-bold border-b border-blue-500 dark:border-blue-400 pb-1 mb-2">教育经历</h2>
                            <div class="flex justify-between">
                                <p class="font-medium">衢州学院</p>
                                <p>2022-2026</p>
                            </div>
                            <p class="text-gray-600 dark:text-gray-400">本科</p>
                        </div>

                        <!-- 竞赛经历 -->
                        <div class="mb-4">
                            <h2 class="text-lg font-bold border-b border-blue-500 dark:border-blue-400 pb-1 mb-2">竞赛经历</h2>
                            <ul class="list-disc pl-4 space-y-1 text-sm">
                                <li>第十七届全国大学生计算机设计大赛国家级三等奖</li>
                                <li>第十七届全国大学生计算机设计大赛省级赛一等奖</li>
                                <li>第十五届蓝桥杯大赛软件赛B组省级三等奖</li>
                                <li>第十四届蓝桥杯大赛软件赛B组省级三等奖</li>
                            </ul>
                        </div>

                        <!-- 校园经历 -->
                        <div class="mb-4">
                            <h2 class="text-lg font-bold border-b border-blue-500 dark:border-blue-400 pb-1 mb-2">校园经历</h2>
                            <p class="text-sm">担任学院实验中心智能之翼实验室负责人一职，负责实验室日常管理，维护。
                                在多次夏季小学期综合实践中，作为项目组长，成功领导团队完成需求分析、分工协作与代码合并，确保项目高效推进，最终荣获“优秀项目”奖。</p>
                        </div>
                    </div>

                    <!-- 右侧栏 -->
                    <div>
                        <!-- 专业技能 -->
                        <div class="mb-4">
                            <h2 class="text-lg font-bold border-b border-blue-500 dark:border-blue-400 pb-1 mb-2">专业技能</h2>
                            <ul class="list-disc pl-4 space-y-1 text-sm">
                                <li>计算机基础：熟悉掌握计算机网络，数据结构和算法，操作系统</li>
                                <li>Java：熟悉Java语言，具备JVM调优和问题排查能力</li>
                                <li>开发工具：熟悉使用Maven，Git，IDEA，Docker等开发工具</li>
                                <li>Linux：熟悉Debian,Ubuntu等Linux发行版本操作，熟悉部署上线流程，熟悉域名解析，SSL证书申请等操作</li>
                                <li>数据库：熟练掌握Mysql,Redis,Elasticsearch使用及常见优化手段</li>
                                <li>框架：熟悉使用Spring,Spring MVC,SpringBoot,SpringCloud,Mybatis,Mybatis Plus等Java开发框架。熟悉使用gin,gorm等Golang开发框架</li>
                                <li>分布式：熟悉分布式相关理论，熟练使用SpringCloud Alibaba全家桶</li>
                                <li>前端：熟悉掌握html,css,javascript,Axios,Vue等前端技术，熟悉AntDesign,Tailwindcss,Animate.css,Motion等Vue开发组件。熟悉前后端分离架构，Restful接口设计</li>
                            </ul>
                        </div>
                    </div>
                </div>

                <!-- 项目经历（跨越两列） -->
                <div>
                    <h2 class="text-lg font-bold border-b border-blue-500 dark:border-blue-400 pb-1 mb-2">项目经历</h2>
                    <div class="space-y-4 text-sm">
                        <!-- 智能之翼打卡平台 -->
                        <div>
                            <h3 class="text-base font-semibold">智能之翼打卡平台</h3>
                            <p class="my-1">简述：为实验中心"智能之翼"实验室成员设计并开发的一站式管理平台。该平台整合了日常打卡、算法训练（在线编程、调试、通过率测试）、周报/文章发布与审阅、成员交流及动态值日表管理等多项功能，旨在提升实验室内部协作效率与管理规范性。</p>
                            <p class="mb-1"><span class="font-medium">技术栈：</span>Spring Boot, Spring Security, Vue, MyBatis, MySQL, Redis</p>
                            <p class="mb-1"><span class="font-medium">个人职责：</span>主导整个项目的技术选型、系统架构设计与模块化规划。独立负责核心后端功能的开发与实现。设计并实现了一套后端服务，用于接收、编译和执行用户提交的算法代码，并实时反馈代码运行结果与通过率。负责数据库设计与维护，实现文章发布、评论互动、权限管理及动态值日表等功能模块。</p>
                            <p><span class="font-medium">项目成果：</span>荣获实验中心实验室项目评审二等奖。项目成功部署上线，并在实验室内部投入实际应用。</p>
                        </div>

                        <!-- AI职探 -->
                        <div>
                            <h3 class="text-base font-semibold">AI职探</h3>
                            <p class="my-1">简述：面向职场新人与企业用户打造的智能化求职服务平台。通过集成大型语言模型（LLM），解决传统简历工具的痛点，提供个性化、智能化的简历生成与优化服务。用户输入关键信息后，系统可结合模板风格进行AI润色生成专业简历。平台亦支持简历在线投递、企业交流及模拟面试功能。</p>
                            <p class="mb-1"><span class="font-medium">技术栈：</span>Spring Boot, Vue, MyBatis, MySQL, Redis, Elasticsearch, WebSocket, JWT</p>
                            <p class="mb-1"><span class="font-medium">个人职责：</span>主导整个项目的技术架构设计、功能模块规划及前后端代码实现。采用WebSocket技术实现用户间即时消息传递和LLM交互的流式响应输出。集成Elasticsearch优化简历信息与招聘岗位的检索性能。负责AI简历生成对接、在线投递、用户认证等核心功能开发。</p>
                            <p><span class="font-medium">项目成果：</span>荣获中国大学生计算机设计大赛国家级三等奖</p>
                        </div>
                        <br>
                        <!-- FlyinSSH -->
                        <div>
                            <h3 class="text-base font-semibold">FlyinSSH</h3>
                            <p class="my-1">简述：为需要管理多台VPS的用户设计开发的Web端一体化管理工具。平台在浏览器端复现了常用SSH桌面客户端的核心功能，支持VPS连接管理、SFTP文件操作，以及通过内置代码编辑器在线修改服务器上的代码和配置文件。</p>
                            <p class="mb-1"><span class="font-medium">技术栈：</span>Spring Boot, Vue, MyBatis, MySQL, Redis, JSch, WebSocket, JWT</p>
                            <p class="mb-1"><span class="font-medium">个人职责：</span>主导项目架构设计与开发实现。设计基于WebSocket的通信方案，实现浏览器与服务器间的SSH隧道。利用JSch实现后端SSH/SFTP功能。创新设计Web端文件实时编辑与保存机制。</p>
                            <p><span class="font-medium">项目成果：</span>成功实现网页端远程服务器管理的核心功能，提供便捷的多服务器Web管理方案。</p>
                        </div>

                        <!-- 智论脉动 -->
                        <div>
                            <h3 class="text-base font-semibold">智论脉动</h3>
                            <p class="my-1">简述：面向高校师生的论文全周期智能辅助平台。通过构建"格式规范校验与智能调整、在线协同编辑与指导、模拟答辩预演、研究数据辅助建模"的闭环服务体系，解决传统论文写作中格式调整繁琐、师生沟通不畅、答辩准备不足等核心痛点。</p>
                            <p class="mb-1"><span class="font-medium">技术栈：</span>Gin, Vue, Gorm, MySQL, Redis, WebSocket, JWT</p>
                            <p class="mb-1"><span class="font-medium">个人职责：</span>主导项目整体技术架构设计及核心功能开发。开发了高度可定制的在线论文编辑器，支持富文本编辑和拖拽式组件管理。实现了论文模板的创建、存储和复用机制，以及精准的Word文档导出功能。构建了基于WebSocket的实时协作系统，支持师生双向选择、在线批注和即时通讯。开发了模拟答辩功能，集成TTS和STT技术，提供全面的答辩预演和评估体验。</p>
                            <p><span class="font-medium">项目成果：</span>显著提升了论文写作和指导效率，为师生提供了一站式论文管理解决方案。计算机设计大赛中已突围校赛，省赛评审中。</p>
                        </div>

                        <!-- 创剧星球 -->
                        <div>
                            <h3 class="text-base font-semibold">创剧星球</h3>
                            <p class="my-1">简述：前沿剧情内容生态平台，融合AI驱动创作流程、多模态内容交互社区及智能化内容管理功能。为创作者提供结构化创作工作流，支持团队协作、版本控制与AI辅助，并支持多格式导出。为读者提供沉浸式的图文、音频、视频等多模态交互体验。</p>
                            <p class="mb-1"><span class="font-medium">技术栈：</span>Gin, Vue, Gorm, MySQL, Redis, WebSocket, JWT, FFMPEG</p>
                            <p class="mb-1"><span class="font-medium">个人职责：</span>主导平台架构设计和核心功能开发。实现了在线创作工作流，包括项目创建、剧本结构规划、富文本编辑等功能。深度集成AIGC能力，提供智能创作辅助。构建了多模态交互社区，支持多种内容形式的展示和交互。开发了实时通知系统和数据可视化大屏，实现精细化运营管理。</p>
                            <p><span class="font-medium">项目成果：</span>打造了完整的创作生态系统，为创作者和读者提供优质的内容创作与消费平台。计算机设计大赛中已突围校赛，省赛评审中。</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>