<template>
  <div class="name-card">
    <div class="avatar-container">
      <img src="/头像.jpg" alt="头像" class="avatar" />
    </div>
    <h1 class="name">边城巷深</h1>
    <div class="job-title">求职意向：Java后端开发</div>

    <el-divider>
      <span class="info-toggle" @click="isInfoExpanded = !isInfoExpanded">
        <span>个人信息</span>
        <el-icon class="toggle-icon" :class="{ expanded: isInfoExpanded }">
          <ArrowRight />
        </el-icon>
      </span>
    </el-divider>

    <el-collapse-transition>
      <div v-show="isInfoExpanded" class="info-section">
        <div class="info-item">
          <el-icon><User /></el-icon>
          <span>男 | 21岁</span>
        </div>
        <div class="info-item">
          <el-icon><Phone /></el-icon>
          <span>18891837322</span>
        </div>
        <div class="info-item">
          <el-icon><Message /></el-icon>
          <span>2185833595@qq.com</span>
        </div>
        <div class="info-item">
          <el-icon><School /></el-icon>
          <span>西北工业大学</span>
        </div>
        <div class="info-item">
          <el-icon><Link /></el-icon>
          <a href="https://github.com/Harryup-lei" target="_blank" class="github-link">
            github.com/Harryup-lei
          </a>
        </div>
      </div>
    </el-collapse-transition>

    <el-divider>
      <span class="info-toggle" @click="isSkillsExpanded = !isSkillsExpanded">
        <span>专业技能</span>
        <el-icon class="toggle-icon" :class="{ expanded: isSkillsExpanded }">
          <ArrowRight />
        </el-icon>
      </span>
    </el-divider>

    <el-collapse-transition>
      <div v-show="isSkillsExpanded" class="skills-section">
        <el-tag
          v-for="(skill, index) in skills"
          :key="index"
          type="info"
          class="skill-tag"
          effect="plain"
        >
          {{ skill }}
        </el-tag>
      </div>
    </el-collapse-transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { ArrowRight } from '@element-plus/icons-vue'

const skills = ref([
  '扎实的计算机基础知识，常用数据结构与算法',
  'Java基础与面向对象编程',
  'JVM底层原理，垃圾回收机制',
  'Java并发编程与线程池',
  'Spring、Spring Boot、MyBatis',
  'MySQL使用与优化',
  'Redis缓存与解决方案',
  '消息队列RabbitMQ',
  '微服务架构',
  'Git、Maven、Docker'
])

const isInfoExpanded = ref(true)
const isSkillsExpanded = ref(true)
</script>

<style scoped>
.name-card {
  background: rgba(255, 255, 255, 0.95);
  border-radius: 20px;
  padding: 40px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(10px);
  max-width: 500px;
  margin: 0 auto;
  text-align: center;
}

.avatar-container {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  overflow: hidden;
  margin: 0 auto 20px;
  border: 4px solid rgba(255, 255, 255, 0.8);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.avatar {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.name {
  font-size: 28px;
  font-weight: 600;
  color: #303133;
  margin-bottom: 8px;
  letter-spacing: 1px;
}

.job-title {
  font-size: 16px;
  color: #606266;
  margin-bottom: 30px;
  font-weight: 500;
}

.info-section {
  margin-bottom: 10px;
}

.info-item {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  margin-bottom: 12px;
  color: #606266;
  font-size: 14px;
}

.info-item .el-icon {
  color: #909399;
}

.github-link {
  color: #409EFF;
  text-decoration: none;
  transition: all 0.3s ease;
}

.github-link:hover {
  color: #66b1ff;
  text-decoration: underline;
}

.info-toggle {
  display: flex;
  align-items: center;
  gap: 6px;
  cursor: pointer;
  user-select: none;
  transition: color 0.3s ease;
}

.info-toggle:hover {
  color: #409EFF;
}

.toggle-icon {
  transition: transform 0.3s ease;
  font-size: 12px;
}

.toggle-icon.expanded {
  transform: rotate(90deg);
}

.skills-section {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  justify-content: center;
}

.skill-tag {
  border-radius: 15px;
  background: rgba(245, 247, 250, 0.8);
  border: 1px solid rgba(220, 223, 230, 0.5);
}

:deep(.el-divider__text) {
  color: #909399;
  font-size: 14px;
}
</style>