<script setup lang="ts">
import { Icon } from '@iconify/vue'
</script>

<template>
  <div class="max-w-4xl mx-auto px-6 lg:px-8 flex flex-col items-start justify-center min-h-[70vh]">
    <div class="mb-6 flex space-x-4">
      <span class="inline-flex items-center rounded-full bg-teal-400/10 px-3 py-1 text-sm font-medium text-teal-400 ring-1 ring-inset ring-teal-400/20">
        AI Engineer
      </span>
      <span class="inline-flex items-center rounded-full bg-blue-400/10 px-3 py-1 text-sm font-medium text-blue-400 ring-1 ring-inset ring-blue-400/20">
        Product Manager
      </span>
    </div>
    
    <h1 class="text-5xl lg:text-7xl font-bold tracking-tight text-white mb-6">
      构建未来的<br/>
      <span class="text-transparent bg-clip-text bg-gradient-to-r from-teal-400 to-blue-500">智能体验</span>。
    </h1>
    
    <p class="mt-4 text-xl text-slate-400 max-w-2xl leading-relaxed">
      你好，我是 xbb。我致力于融合产品思维与前沿AI技术，打造卓越的用户体验。在 RAG, Agent 和 AI Coding 领域不断探索。
    </p>
    
    <div class="mt-10 flex space-x-6">
      <RouterLink to="/projects" class="rounded-md bg-teal-500 px-6 py-3 text-lg font-semibold text-white shadow-sm hover:bg-teal-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-teal-500 transition-all">
        查看项目
      </RouterLink>
      <a href="https://github.com" target="_blank" class="rounded-md bg-white/10 px-6 py-3 text-lg font-semibold text-white shadow-sm hover:bg-white/20 transition-all flex items-center">
        <Icon icon="mdi:github" class="w-6 h-6 mr-2" />
        GitHub
      </a>
    </div>

    <!-- Tech Stack Preview -->
    <div class="mt-24 w-full border-t border-slate-800 pt-8">
      <p class="text-sm font-semibold tracking-wide text-slate-500 uppercase mb-6">技术栈与专长</p>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-6 text-slate-400">
        <div class="flex items-center space-x-2">
          <Icon icon="mdi:robot-outline" class="w-6 h-6 text-teal-400" />
          <span>AI Agents</span>
        </div>
        <div class="flex items-center space-x-2">
          <Icon icon="mdi:database-search" class="w-6 h-6 text-blue-400" />
          <span>RAG Systems</span>
        </div>
        <div class="flex items-center space-x-2">
          <Icon icon="mdi:vuejs" class="w-6 h-6 text-green-400" />
          <span>Vue 3 / Frontend</span>
        </div>
        <div class="flex items-center space-x-2">
          <Icon icon="mdi:lightbulb-on" class="w-6 h-6 text-yellow-400" />
          <span>Product Strategy</span>
        </div>
      </div>
    </div>
  </div>
</template>
