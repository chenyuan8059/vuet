<template>
  <!-- 设置指令监听全局滚动条 -->
  <div v-route-scroll.window="{ path: 'topic-list' }">
    <header>
      <ul>
        <li v-for="item in list.tabs">
          <router-link :to="{ name: 'topic-list', query: { tab: item.value } }">{{ item.label }}</router-link>
        </li>
      </ul>
    </header>
    <ul class="list">
      <li v-for="item in list.data">
          <router-link :to="{ name: 'topic-detail', params: { id: item.id } }">{{ item.title }}</router-link>
      </li>
    </ul>
  </div>
</template>
<script>
  import { mapRules, mapModules } from 'vuet'

  export default {
    mixins: [
      // 设置模块的更新规则
      mapRules({
        route: 'topic-list'
      }),
      // 连接模块的状态
      mapModules({
        list: 'topic-list'
      })
    ]
  }
</script>
<style scoped>

</style>
