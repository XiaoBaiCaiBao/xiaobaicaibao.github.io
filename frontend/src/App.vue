<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}
</script>

<template>
  <div class="min-h-screen bg-slate-900 text-slate-200 font-sans selection:bg-teal-300 selection:text-teal-900">
    <header class="fixed top-0 left-0 right-0 z-50 bg-slate-900/80 backdrop-blur-md border-b border-slate-800">
      <div class="max-w-6xl mx-auto px-6 py-4 flex justify-between items-center">
        <!-- Logo -->
        <RouterLink to="/" class="text-2xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-teal-400 to-blue-500">
          xbb.dev
        </RouterLink>

        <!-- Desktop Navigation -->
        <nav class="hidden md:flex space-x-8">
          <RouterLink to="/" class="text-sm font-medium text-slate-400 hover:text-teal-300 transition-colors" active-class="text-teal-400">首页</RouterLink>
          <RouterLink to="/about" class="text-sm font-medium text-slate-400 hover:text-teal-300 transition-colors" active-class="text-teal-400">关于我</RouterLink>
          <RouterLink to="/blog" class="text-sm font-medium text-slate-400 hover:text-teal-300 transition-colors" active-class="text-teal-400">博客</RouterLink>
          <RouterLink to="/business" class="text-sm font-medium text-slate-400 hover:text-teal-300 transition-colors" active-class="text-teal-400">业务</RouterLink>
          <RouterLink to="/projects" class="text-sm font-medium text-slate-400 hover:text-teal-300 transition-colors" active-class="text-teal-400">项目</RouterLink>
        </nav>

        <!-- Mobile Menu Button -->
        <button @click="toggleMobileMenu" class="md:hidden text-slate-400 hover:text-white focus:outline-none">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>

      <!-- Mobile Navigation -->
      <nav v-if="isMobileMenuOpen" class="md:hidden bg-slate-800 border-b border-slate-700 px-6 py-4 space-y-4">
        <RouterLink @click="toggleMobileMenu" to="/" class="block text-base font-medium text-slate-300 hover:text-teal-300" active-class="text-teal-400">首页</RouterLink>
        <RouterLink @click="toggleMobileMenu" to="/about" class="block text-base font-medium text-slate-300 hover:text-teal-300" active-class="text-teal-400">关于我</RouterLink>
        <RouterLink @click="toggleMobileMenu" to="/blog" class="block text-base font-medium text-slate-300 hover:text-teal-300" active-class="text-teal-400">博客</RouterLink>
        <RouterLink @click="toggleMobileMenu" to="/business" class="block text-base font-medium text-slate-300 hover:text-teal-300" active-class="text-teal-400">业务</RouterLink>
        <RouterLink @click="toggleMobileMenu" to="/projects" class="block text-base font-medium text-slate-300 hover:text-teal-300" active-class="text-teal-400">项目</RouterLink>
      </nav>
    </header>

    <!-- Main Content -->
    <main class="pt-24 min-h-[calc(100vh-80px)]">
      <RouterView />
    </main>
    
    <!-- Footer -->
    <footer class="py-8 text-center text-slate-500 text-sm border-t border-slate-800 mt-12">
      <p>© {{ new Date().getFullYear() }} xbb. All rights reserved.</p>
    </footer>
  </div>
</template>

<style>
/* 可以在这里添加一些全局动画或特定的样式 */
</style>
