<template>
  <div>Page 2</div>

  <div>
    <DxDataGrid>
      <DxColumn caption="Test" />
    </DxDataGrid>
  </div>

  <div>
    <Comp />
  </div>
</template>

<script setup lang="ts">
import { DxDataGrid, DxColumn } from 'devextreme-vue/data-grid';
import { h, ref } from 'vue';
import SlowComponent from '../components/SlowComponent.vue';

const Comp = (props: any, context: any) => {
  return h(SlowComponent);
};
</script>
