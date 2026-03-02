<template>
  <div class="layout-container">
    <header class="header">
      <h2>LangCanvas AI智能低代码画布</h2>
      <el-button type="primary" plain circle @click="toggleChat">🤖</el-button>
    </header>

    <main class="main-content">
      <section class="canvas-area" :style="{width: showChat ? '70%' : '100%'}">
        <div class="empty-tip">
          <h3>画布</h3>
          <p></p>
        </div>
      </section>

      <section class="chat-area">
        <div class="chat-box">
          <h3>AI对话页面</h3>
          <p></p>
          <div class="input-area">
            <el-input placeholder="请告诉AI你想生成什么组件"></el-input>
            <el-button type="success">发送</el-button>
          </div>
        </div>

      </section>
    </main>
  </div>

</template>

<script setup>
import { ref } from 'vue';

const showChat = ref(false);
const toggleChat = () => {
  showChat.value = !showChat.value;
}

</script>



<style scoped>

.layout-container{
  height: 100vh;
  display: flex;
  flex-direction: column;
  margin: 0;
  font-family: Arial,sans-serif;
  
}

.header{
  height: 50px;
  background-color: #7eaee1;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.main-content{
  flex:1; /*占剩下的全部空间 */
  display: flex;
  background-color: #f0f2f5;
  overflow: hidden;
}

.canvas-area{
  transition: width 0.3s; /* 宽度变化时有个平滑的动画 */
  padding: 20px;
  border: 1px solid #ddd;

}

.empty-tip{
  height: 100%;
  background: white;
  border: 2px dashed #ccc;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #999;
}


.chat-box{
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  
}

.input-area {
    display: flex;
  }


</style>