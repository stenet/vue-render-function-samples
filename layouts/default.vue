<template>
  <div class="flex gap-4">
    <NuxtLink to="/page1">Page 1</NuxtLink>
    <NuxtLink to="/page2">Page 2</NuxtLink>
    <NuxtLink to="/page3">Page 3</NuxtLink>
    <NuxtLink to="/page4">Page 4</NuxtLink>
    <NuxtLink to="/page5">Page 5</NuxtLink>
    <NuxtLink to="/page6">Page 6</NuxtLink>
  </div>
  <div class="font-semibold text-lg py-6">
    <h2>Default</h2>
  </div>
  <div>
    <NuxtErrorBoundary>
      <slot></slot>
      <template #error="{ error }">
        <p>Ein Fehler ist aufgetreten :(</p>
        <p>{{ error }}</p>
        <button
          class="border border-neutral-200"
          @click="handleRetryClick(error)"
        >
          nochmal versuchen
        </button>
      </template>
    </NuxtErrorBoundary>
  </div>
</template>

<script setup lang="ts">
import { nextTick } from 'vue';

function handleRetryClick(error: any) {
  error.value = null;
  navigateTo('/');
}
</script>
