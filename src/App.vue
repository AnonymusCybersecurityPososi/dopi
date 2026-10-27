<script setup lang="ts">
import { ref } from 'vue'
import ThemeController from './components/ThemeController.vue'
import ProfileCard from './components/ProfileCard.vue'

// Управління станом алерта строго через ref (без таймерів)
const isAlertVisible = ref(false)

const toggleLike = () => {
  isAlertVisible.value = !isAlertVisible.value
}
</script>

<template>
  <div class="min-h-screen bg-base-200 p-8 flex flex-col items-center gap-8">
    
    <header class="w-full max-w-4xl flex justify-end">
      <ThemeController />
    </header>

    <main class="flex flex-col items-center gap-6 relative">
      
      <!-- Анімація через вбудований компонент Transition -->
      <Transition name="fade">
        <div v-if="isAlertVisible" class="alert alert-success absolute -top-20 w-auto">
          <span>Успішно! Ви оновили статус профілю.</span>
        </div>
      </Transition>

      <ProfileCard>
        <template #avatar>
          <div class="w-16 rounded-full bg-base-300 ring ring-primary ring-offset-base-100 ring-offset-2">
            <img src="https://i.pravatar.cc/150?img=11" alt="Avatar" />
          </div>
        </template>
        
        <template #badge>
          Студент АТ
          <div class="badge badge-primary">PRO</div>
        </template>
        
        <template #default>
          <p>Привіт! Я вивчаю Vue 3 Composition API та Tailwind CSS. Мені подобається створювати інтерактивні інтерфейси без хардкоду кольорів.</p>
        </template>
        
        <template #actions>
          <button class="btn btn-secondary" @click="toggleLike">
            {{ isAlertVisible ? 'Приховати статус' : 'Оновити статус' }}
          </button>
        </template>
      </ProfileCard>

    </main>
  </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>