<script setup lang="ts">
</script>

<template>
  <div class="max-w-4xl mx-auto px-6 lg:px-8 py-12">
    <h1 class="text-4xl font-bold tracking-tight text-white sm:text-5xl mb-12">关于我</h1>
    
    <div class="space-y-16">
      <section>
        <h2 class="text-2xl font-semibold text-teal-400 mb-6 flex items-center">
          <span class="w-8 h-px bg-teal-400/50 mr-4"></span>
          个人介绍
        </h2>
        <div class="prose prose-invert lg:prose-lg text-slate-400">
          <p class="leading-relaxed mb-6">
            我是一名充满热情的 AI 工程师与产品经理。我相信技术应该服务于人，而不仅仅是为了技术的堆砌。在我的职业生涯中，我始终致力于在技术深度和产品体验之间找到最佳平衡点。
          </p>
          <p class="leading-relaxed">
            我的名字是 xbb。我专注于构建智能系统，探索人工智能如何改变我们的工作和生活方式。
          </p>
        </div>
      </section>

      <section>
        <h2 class="text-2xl font-semibold text-blue-400 mb-6 flex items-center">
          <span class="w-8 h-px bg-blue-400/50 mr-4"></span>
          过往经历
        </h2>
        
        <div class="space-y-8 border-l-2 border-slate-800 ml-3 pl-8">
          <div class="relative">
            <div class="absolute w-4 h-4 bg-blue-500 rounded-full -left-[41px] top-1.5 border-4 border-slate-900"></div>
            <h3 class="text-xl font-medium text-white">高级产品经理 / AI 工程师</h3>
            <p class="text-sm text-teal-300 mt-1 font-mono">2022 - 至今</p>
            <p class="mt-3 text-slate-400 leading-relaxed">
              主导了多个基于大语言模型的核心产品研发，包括智能客服系统、企业内部知识库问答(RAG)和自动化编码助手。推动团队从传统开发模式向 AI 驱动研发转型。
            </p>
          </div>

          <div class="relative">
            <div class="absolute w-4 h-4 bg-slate-600 rounded-full -left-[41px] top-1.5 border-4 border-slate-900"></div>
            <h3 class="text-xl font-medium text-slate-300">全栈开发工程师</h3>
            <p class="text-sm text-slate-500 mt-1 font-mono">2019 - 2022</p>
            <p class="mt-3 text-slate-400 leading-relaxed">
              负责企业级 SaaS 平台的前后端架构设计与核心模块开发。优化了大规模数据渲染性能，提升了系统整体响应速度和用户满意度。
            </p>
          </div>
        </div>
      </section>

      <section>
        <h2 class="text-2xl font-semibold text-purple-400 mb-6 flex items-center">
          <span class="w-8 h-px bg-purple-400/50 mr-4"></span>
          Contact Me
        </h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
          <a href="mailto:hello@example.com" class="p-6 rounded-2xl bg-slate-800/50 border border-slate-700/50 hover:border-purple-500/50 hover:bg-slate-800 transition-all group">
            <div class="text-slate-400 group-hover:text-purple-400 mb-2">Email</div>
            <div class="text-white font-medium">hello@example.com</div>
          </a>
          <a href="https://twitter.com" target="_blank" class="p-6 rounded-2xl bg-slate-800/50 border border-slate-700/50 hover:border-blue-400/50 hover:bg-slate-800 transition-all group">
            <div class="text-slate-400 group-hover:text-blue-400 mb-2">Twitter</div>
            <div class="text-white font-medium">@xbb_dev</div>
          </a>
          <a href="https://github.com" target="_blank" class="p-6 rounded-2xl bg-slate-800/50 border border-slate-700/50 hover:border-slate-300/50 hover:bg-slate-800 transition-all group">
            <div class="text-slate-400 group-hover:text-slate-300 mb-2">GitHub</div>
            <div class="text-white font-medium">github.com/xbb</div>
          </a>
        </div>
      </section>
    </div>
  </div>
</template>
