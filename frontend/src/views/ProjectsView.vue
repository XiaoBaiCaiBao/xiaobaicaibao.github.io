<script setup lang="ts">
import { ref, computed } from 'vue'
import { Icon } from '@iconify/vue'

const categories = ['全部', 'AI客服', 'RAG应用', '开发工具']
const currentCategory = ref('全部')

const projects = [
  {
    id: 1,
    title: 'OmniChat AI',
    description: '全渠道智能客服平台。集成大语言模型，支持网页、微信、应用内消息等多种渠道的无缝接入与自动应答。',
    icon: 'mdi:robot-excited-outline',
    category: 'AI客服',
    techStack: ['Vue 3', 'Node.js', 'LLM', 'WebSockets'],
    github: '#',
    demo: '#'
  },
  {
    id: 2,
    title: 'Enterprise Knowledge Hub',
    description: '基于 RAG 架构的企业级知识检索问答系统。支持多种文档格式解析、混合检索与高精度问答生成。',
    icon: 'mdi:database-search-outline',
    category: 'RAG应用',
    techStack: ['Python', 'LangChain', 'Pinecone', 'React'],
    github: '#',
    demo: '#'
  },
  {
    id: 3,
    title: 'CodePilot CLI',
    description: '一款基于终端的 AI 辅助编码工具。自动分析本地代码库，生成提交信息，协助进行代码审查。',
    icon: 'mdi:console-line',
    category: '开发工具',
    techStack: ['TypeScript', 'Commander', 'OpenAI API'],
    github: '#',
    demo: '#'
  },
  {
    id: 4,
    title: 'SkillBuilder for Cursor',
    description: '快速生成和管理 Cursor AI 编辑器自定义 Skills 规则的可视化工具，提升团队协作效率。',
    icon: 'mdi:puzzle-outline',
    category: '开发工具',
    techStack: ['Vue 3', 'Tailwind', 'Vite'],
    github: '#',
    demo: '#'
  }
]

const filteredProjects = computed(() => {
  if (currentCategory.value === '全部') {
    return projects
  }
  return projects.filter(proj => proj.category === currentCategory.value)
})
</script>

<template>
  <div class="max-w-6xl mx-auto px-6 lg:px-8 py-12 flex flex-col md:flex-row gap-12 relative">
    
    <!-- 左侧二级导航 -->
    <aside class="w-full md:w-64 flex-shrink-0">
      <div class="sticky top-24">
        <h2 class="text-xl font-bold text-white mb-6 pl-4 border-l-2 border-purple-500">项目分类</h2>
        <nav class="flex flex-row md:flex-col gap-2 overflow-x-auto pb-4 md:pb-0 hide-scrollbar">
          <button 
            v-for="cat in categories" :key="cat"
            @click="currentCategory = cat"
            class="whitespace-nowrap px-4 py-2 text-left rounded-lg text-sm font-medium transition-all"
            :class="[
              currentCategory === cat 
                ? 'bg-slate-800 text-purple-400 shadow-sm border border-slate-700/50' 
                : 'text-slate-400 hover:bg-slate-800/50 hover:text-slate-200 border border-transparent'
            ]"
          >
            {{ cat }}
          </button>
        </nav>
      </div>
    </aside>

    <!-- 右侧项目列表 -->
    <div class="flex-1 min-w-0">
      <div class="mb-12">
        <h1 class="text-4xl font-bold tracking-tight text-white mb-4">项目</h1>
        <p class="text-lg text-slate-400">展示我近期开发的一些开源工具和核心业务应用。</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div 
          v-for="proj in filteredProjects" :key="proj.id"
          class="bg-slate-800/20 rounded-2xl border border-slate-700 p-6 hover:border-purple-500/50 transition-all flex flex-col h-full relative overflow-hidden group"
        >
          <!-- 装饰性背景光晕 -->
          <div class="absolute top-0 right-0 w-32 h-32 bg-purple-500/10 rounded-full blur-3xl -mr-16 -mt-16 group-hover:bg-purple-500/20 transition-all"></div>

          <div class="relative z-10 flex flex-col h-full">
            <div class="flex items-start justify-between mb-4">
              <div class="w-12 h-12 bg-purple-500/10 rounded-xl flex items-center justify-center">
                <Icon :icon="proj.icon" class="w-7 h-7 text-purple-400" />
              </div>
              <div class="flex space-x-3">
                <a :href="proj.github" target="_blank" class="text-slate-400 hover:text-white transition-colors" title="View Source">
                  <Icon icon="mdi:github" class="w-6 h-6" />
                </a>
                <a :href="proj.demo" target="_blank" class="text-slate-400 hover:text-white transition-colors" title="Live Demo">
                  <Icon icon="mdi:open-in-new" class="w-6 h-6" />
                </a>
              </div>
            </div>
            
            <h3 class="text-xl font-bold text-slate-200 mb-2">{{ proj.title }}</h3>
            <p class="text-sm text-slate-400 mb-6 flex-grow leading-relaxed">
              {{ proj.description }}
            </p>
            
            <div class="flex flex-wrap gap-2 mt-auto pt-4 border-t border-slate-700/50">
              <span v-for="tech in proj.techStack" :key="tech" class="text-xs font-medium text-slate-300 bg-slate-800 px-2.5 py-1 rounded-md border border-slate-700">
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
      
      <div v-if="filteredProjects.length === 0" class="text-center py-20 text-slate-500">
        该分类下暂无项目。
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
