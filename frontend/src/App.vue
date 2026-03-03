<template>
  <RenderEngine :schema="testSchema" />
</template>

<script setup>
import RenderEngine from './components/RenderEngine.vue'
import { ref } from 'vue'

const testSchema = ref([
  {
    id: '1',
    type: 'el-card',
    props: { header: '卡片1' },
    children: [
      { id: '1-1', type: 'el-button', props: { type: 'primary' } }
    ]
  },
  {
    id: '2',
    type: 'el-button',
    props: { type: 'success' }
  }
])
</script>