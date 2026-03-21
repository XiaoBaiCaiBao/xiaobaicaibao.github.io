<script setup lang="ts">
import { ref, computed } from 'vue'
import { Icon } from '@iconify/vue'

const categories = ['全部', '客服', 'CRM', '虚拟陪伴', '音乐']
const currentCategory = ref('全部')

const businesses = [
  {
    id: 1,
    title: '智能客服解决方案',
    description: '基于大语言模型的全天候智能客服系统，支持多轮对话、情感分析与自动工单生成，提升客户满意度并降低人工成本。',
    icon: 'mdi:headset',
    category: '客服',
    features: ['7x24小时在线', '知识库自动更新', '多模态交互']
  },
  {
    id: 2,
    title: '招聘 CRM 系统',
    description: '面向中大型企业的智能招聘管理平台，利用 AI 简历解析、人岗匹配算法，大幅提高 HR 筛选与沟通效率。',
    icon: 'mdi:account-group',
    category: 'CRM',
    features: ['简历一键解析', 'AI 智能匹配', '自动化流程']
  },
  {
    id: 3,
    title: '企业黄页目录',
    description: '结构化的企业信息管理与检索系统，集成企业图谱分析，帮助销售团队快速定位目标客户。',
    icon: 'mdi:book-open-page-variant',
    category: 'CRM',
    features: ['企业图谱', '精准搜索', '数据可视化']
  },
  {
    id: 4,
    title: '个性化虚拟陪伴',
    description: '定制化情感陪伴 AI，具备长期记忆与个性化人设，适用于情感支持、心理辅导等场景。',
    icon: 'mdi:heart-pulse',
    category: '虚拟陪伴',
    features: ['情感共鸣', '长期记忆', '多角色设定']
  },
  {
    id: 5,
    title: '声乐评测与辅助系统',
    description: '结合音频信号处理与 AI 模型的在线声乐学习工具，提供音准、节奏等维度的实时反馈。',
    icon: 'mdi:microphone',
    category: '音乐',
    features: ['实时音准分析', '节奏评测', '发音纠正']
  },
  {
    id: 6,
    title: '智能钢琴伴奏',
    description: '根据旋律自动生成和声与伴奏织体，支持多种风格转换，辅助音乐创作与练习。',
    icon: 'mdi:piano',
    category: '音乐',
    features: ['自动和声', '风格迁移', 'MIDI 导出']
  },
  {
    id: 7,
    title: '吉他谱智能生成',
    description: '上传音频即可自动转写为吉他六线谱（Tab），并推荐适合的指法与和弦编配。',
    icon: 'mdi:guitar-acoustic',
    category: '音乐',
    features: ['音频转谱', '智能指法', '多轨导出']
  }
]

const filteredBusinesses = computed(() => {
  if (currentCategory.value === '全部') {
    return businesses
  }
  return businesses.filter(biz => {
    // 处理二级分类：CRM 包含招聘和黄页，音乐包含声乐、钢琴、吉他
    if (currentCategory.value === 'CRM' && ['CRM'].includes(biz.category)) return true;
    if (currentCategory.value === '音乐' && ['音乐'].includes(biz.category)) return true;
    return biz.category === currentCategory.value
  })
})
</script>

<template>
  <div class="max-w-6xl mx-auto px-6 lg:px-8 py-12 flex flex-col md:flex-row gap-12 relative">
    
    <!-- 左侧二级导航 -->
    <aside class="w-full md:w-64 flex-shrink-0">
      <div class="sticky top-24">
        <h2 class="text-xl font-bold text-white mb-6 pl-4 border-l-2 border-blue-500">业务板块</h2>
        <nav class="flex flex-row md:flex-col gap-2 overflow-x-auto pb-4 md:pb-0 hide-scrollbar">
          <button 
            v-for="cat in categories" :key="cat"
            @click="currentCategory = cat"
            class="whitespace-nowrap px-4 py-2 text-left rounded-lg text-sm font-medium transition-all"
            :class="[
              currentCategory === cat 
                ? 'bg-slate-800 text-blue-400 shadow-sm border border-slate-700/50' 
                : 'text-slate-400 hover:bg-slate-800/50 hover:text-slate-200 border border-transparent'
            ]"
          >
            {{ cat }}
          </button>
        </nav>
      </div>
    </aside>

    <!-- 右侧业务列表 -->
    <div class="flex-1 min-w-0">
      <div class="mb-12">
        <h1 class="text-4xl font-bold tracking-tight text-white mb-4">业务</h1>
        <p class="text-lg text-slate-400">涵盖企业服务、娱乐陪伴与在线教育的综合性数字解决方案。</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div 
          v-for="biz in filteredBusinesses" :key="biz.id"
          class="bg-slate-800/40 rounded-3xl p-8 border border-slate-700/50 hover:border-blue-500/50 transition-all hover:-translate-y-1 hover:shadow-xl hover:shadow-blue-900/20 group"
        >
          <div class="w-14 h-14 bg-blue-500/10 rounded-2xl flex items-center justify-center mb-6 group-hover:bg-blue-500/20 transition-colors">
            <Icon :icon="biz.icon" class="w-8 h-8 text-blue-400" />
          </div>
          
          <h3 class="text-2xl font-bold text-slate-200 mb-3 group-hover:text-blue-400 transition-colors">{{ biz.title }}</h3>
          <p class="text-slate-400 mb-6 leading-relaxed line-clamp-3">
            {{ biz.description }}
          </p>
          
          <ul class="space-y-2">
            <li v-for="feat in biz.features" :key="feat" class="flex items-center text-sm text-slate-300">
              <Icon icon="mdi:check-circle-outline" class="w-4 h-4 text-teal-400 mr-2 flex-shrink-0" />
              {{ feat }}
            </li>
          </ul>
        </div>
      </div>
      
      <div v-if="filteredBusinesses.length === 0" class="text-center py-20 text-slate-500">
        该分类下暂无业务。
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
