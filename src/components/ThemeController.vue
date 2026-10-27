<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Список доступных тем согласно заданию
const themes = ['light', 'dark', 'cyberpunk', 'retro']
const currentTheme = ref('light')

const switchTheme = (theme: string) => {
  currentTheme.value = theme
  // Меняем атрибут на уровне тега <html>
  document.documentElement.setAttribute('data-theme', theme)
}

// Устанавливаем тему по умолчанию при монтировании
onMounted(() => {
  switchTheme(currentTheme.value)
})
</script>

<template>
  <div class="dropdown dropdown-end">
    <div tabindex="0" role="button" class="btn m-1">Вибрати тему ({{ currentTheme }})</div>
    <ul tabindex="0" class="dropdown-content z-[1] menu p-2 shadow bg-base-200 rounded-box w-52">
      <li v-for="theme in themes" :key="theme">
        <a @click="switchTheme(theme)" :class="{ 'active': currentTheme === theme }">
          {{ theme }}
        </a>
      </li>
    </ul>
  </div>
</template>