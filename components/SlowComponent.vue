<template>
  <div>
    <div>hello from the other side</div>
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
await new Promise((resolve) => {
  setTimeout(resolve, 2000);
});
</script>
