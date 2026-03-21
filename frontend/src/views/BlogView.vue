<script setup lang="ts">
import { ref, computed } from 'vue'

const categories = ['全部', 'Coding', '产品经理', 'AI']
const currentCategory = ref('全部')

const blogPosts = [
  {
    id: 1,
    title: '深入理解 RAG 系统架构设计',
    summary: '检索增强生成（Retrieval-Augmented Generation）技术正在重塑企业知识库，本文将详细拆解一个生产级 RAG 系统的核心组件与技术选型。',
    date: '2023-11-15',
    category: 'AI',
    tags: ['RAG', 'LLM', '架构']
  },
  {
    id: 2,
    title: '基于 Agent 的多模型协作机制',
    summary: '探讨在复杂业务场景下，如何设计多 Agent 协作框架，以及任务分解、状态管理和冲突解决的实践经验。',
    date: '2023-10-28',
    category: 'AI',
    tags: ['Agent', '协作']
  },
  {
    id: 3,
    title: '从需求文档到可执行代码：MCP 协议探索',
    summary: 'Model Context Protocol (MCP) 为大模型提供了一种标准化的工具调用方式，我们来看看它是如何改变 AI 编码流程的。',
    date: '2023-09-12',
    category: 'AI',
    tags: ['MCP', 'AI Coding']
  },
  {
    id: 4,
    title: 'Vue 3 组件库设计模式与最佳实践',
    summary: '从零开始构建企业级 Vue 3 组件库，包括组件封装、样式隔离、文档生成以及自动化测试的完整指南。',
    date: '2023-08-05',
    category: 'Coding',
    tags: ['Vue', '组件库', '前端']
  },
  {
    id: 5,
    title: 'OpenClaw 项目复盘：如何打造开源 AI 工具',
    summary: '分享 OpenClaw 项目从 0 到 1 的开源历程，包括社区建设、代码规范、版本发布策略等经验。',
    date: '2023-07-20',
    category: 'AI',
    tags: ['OpenClaw', '开源']
  },
  {
    id: 6,
    title: 'AI 时代的产品经理技能图谱',
    summary: '当 AI 成为基础设施，产品经理需要掌握哪些新技能？如何将技术边界与用户需求更好地结合？',
    date: '2023-06-18',
    category: '产品经理',
    tags: ['产品设计', 'AI产品']
  },
  {
    id: 7,
    title: '提升 AI 编码助手的 Skills 设计技巧',
    summary: '在 Cursor 等 AI IDE 中，设计高质量的 Skills（指令模板）是提高开发效率的关键，这里总结了 10 条黄金法则。',
    date: '2023-05-10',
    category: 'AI',
    tags: ['AI Coding', 'Skills', 'Prompt']
  }
]

const filteredPosts = computed(() => {
  if (currentCategory.value === '全部') {
    return blogPosts
  }
  return blogPosts.filter(post => post.category === currentCategory.value)
})
</script>

<template>
  <div class="max-w-6xl mx-auto px-6 lg:px-8 py-12 flex flex-col md:flex-row gap-12 relative">
    
    <!-- 左侧二级导航（移动端置顶） -->
    <aside class="w-full md:w-64 flex-shrink-0">
      <div class="sticky top-24">
        <h2 class="text-xl font-bold text-white mb-6 pl-4 border-l-2 border-teal-500">分类目录</h2>
        <nav class="flex flex-row md:flex-col gap-2 overflow-x-auto pb-4 md:pb-0 hide-scrollbar">
          <button 
            v-for="cat in categories" :key="cat"
            @click="currentCategory = cat"
            class="whitespace-nowrap px-4 py-2 text-left rounded-lg text-sm font-medium transition-all"
            :class="[
              currentCategory === cat 
                ? 'bg-slate-800 text-teal-400 shadow-sm border border-slate-700/50' 
                : 'text-slate-400 hover:bg-slate-800/50 hover:text-slate-200 border border-transparent'
            ]"
          >
            {{ cat }}
          </button>
        </nav>
      </div>
    </aside>

    <!-- 右侧博客列表 -->
    <div class="flex-1 min-w-0">
      <div class="mb-12">
        <h1 class="text-4xl font-bold tracking-tight text-white mb-4">博客</h1>
        <p class="text-lg text-slate-400">分享关于编码、产品设计与人工智能的思考与实践。</p>
      </div>

      <div class="space-y-12">
        <article 
          v-for="post in filteredPosts" :key="post.id"
          class="group relative flex flex-col items-start justify-between bg-slate-800/30 p-8 rounded-2xl border border-slate-700/50 hover:border-teal-500/50 transition-colors"
        >
          <div class="flex items-center gap-x-4 text-xs mb-4">
            <time :datetime="post.date" class="text-slate-500 font-mono">{{ post.date }}</time>
            <span class="relative z-10 rounded-full bg-slate-800 px-3 py-1.5 font-medium text-slate-300 border border-slate-700">
              {{ post.category }}
            </span>
          </div>
          
          <div class="group relative">
            <h3 class="mt-3 text-2xl font-semibold leading-6 text-slate-200 group-hover:text-teal-400 transition-colors">
              <a href="#">
                <span class="absolute inset-0"></span>
                {{ post.title }}
              </a>
            </h3>
            <p class="mt-5 line-clamp-3 text-sm leading-6 text-slate-400">{{ post.summary }}</p>
          </div>

          <div class="mt-6 flex gap-2 flex-wrap">
            <span v-for="tag in post.tags" :key="tag" class="text-xs text-teal-500/80 bg-teal-500/10 px-2 py-1 rounded">
              #{{ tag }}
            </span>
          </div>
        </article>
      </div>
      
      <div v-if="filteredPosts.length === 0" class="text-center py-20 text-slate-500">
        该分类下暂无文章。
      </div>
    </div>
  </div>
</template>

<style scoped>
.hide-scrollbar::-webkit-scrollbar {
  display: none;
}
.hide-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>
