<script setup lang="ts">
// Компонент является сугубо презентационным и служит оберткой для слотов
</script>

<template>
  <div class="card w-96 bg-base-100 shadow-xl">
    <div class="card-body">
      <div class="flex items-center gap-4 mb-4">
        <!-- Іменований слот для кастомного аватара -->
        <div class="avatar">
          <slot name="avatar"></slot>
        </div>
        
        <h2 class="card-title">
          <!-- Іменований слот для статусного бейджа -->
          <slot name="badge"></slot>
        </h2>
      </div>
      
      <div class="text-base-content">
        <!-- Дефолтний слот для опису / біографії -->
        <slot></slot>
      </div>
      
      <div class="card-actions justify-end mt-4">
        <!-- Іменований слот для кнопок взаємодії -->
        <slot name="actions"></slot>
      </div>
    </div>
  </div>
</template>