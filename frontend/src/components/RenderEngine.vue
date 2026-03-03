<template>
  <draggable :list="schema" item-key="id" group="components" class="drag-area">
    <!-- #item 是作用域插槽，element 就是当前循环的元素。 -->
    <template #item="{ element }">
      <div class="component-box">
        <component :is="element.type" v-bind="element.props">
          <!-- <component :is="..."> 是一个动态组件，它可以根据 is 的值动态地渲染不同的组件。 -->
          <!-- v-bind="element.props" 会把 element.props 里的所有属性传给动态组件 -->
          <!-- 如果有children，就组件自己调用自己，组件递归 -->
          <template v-if="element.children">
            <RenderEngine :schema="element.children" />
          </template>
          
        </component>

      </div>
    </template>
  </draggable>
</template>

<script setup>
import draggable from 'vuedraggable'
/*
接收外部传来的图纸（Schema）
组件输入
{
  id: '1',                // 唯一标识，拖拽库需要
  type: 'el-button',       // 组件名
  props: { type: 'primary' }, // 传给组件的属性
  children: [ ... ]        // 子组件（可选）
}
*/
defineProps({
  schema: {
    type: Array,
    required: true
  }
})
</script>

<style scoped>
/* 给拖拽区域加个虚线框，方便我们看清楚扔在哪里 */
.drag-area {
  min-height: 50px;
  padding: 10px;
  border: 1px dashed #ccc;
  background-color: #fafafa;
}
.component-box {
  margin-bottom: 5px;
  cursor: move; /* 鼠标放上去变成十字拖拽图标 */
}
</style>