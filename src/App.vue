

<template>
  <div class="min-h-screen bg-gray-50">
    <!-- 顶部导航 -->
    <header class="bg-white shadow-sm fixed w-full z-10">
      <div class="flex justify-between items-center px-6 h-16">
        <div class="flex items-center">
          <h1 class="text-2xl font-['Pacifico'] text-blue-600">logo</h1>
        </div>
        <div class="flex items-center space-x-4">
          <div class="relative">
            <button class="!rounded-button relative">
              <i class="fas fa-bell text-gray-600"></i>
              <span class="absolute -top-1 -right-1 bg-red-500 text-white text-xs rounded-full w-4 h-4 flex items-center justify-center">3</span>
            </button>
          </div>
          <div class="flex items-center">
            <img :src="avatarUrl" alt="用户头像" class="w-8 h-8 rounded-full" />
            <span class="ml-2 text-gray-700">张经理</span>
          </div>
          <button class="!rounded-button bg-gray-100 px-3 py-1 text-gray-600 hover:bg-gray-200">
            <i class="fas fa-sign-out-alt mr-1"></i>退出
          </button>
        </div>
      </div>
    </header>

    <!-- 主体内容 -->
    <div class="flex pt-16">
      <!-- 左侧菜单 -->
      <aside class="w-64 fixed h-[calc(100vh-4rem)] bg-white shadow-sm">
        <nav class="py-4">
          <template v-for="(item, index) in menuItems" :key="index">
            <div 
              :class="['flex items-center px-6 py-3 cursor-pointer hover:bg-blue-50', 
                      activeMenu === item.key ? 'bg-blue-50 text-blue-600' : 'text-gray-600']"
              @click="activeMenu = item.key"
            >
              <i :class="['fas', item.icon, 'w-5']"></i>
              <span class="ml-3">{{ item.label }}</span>
            </div>
          </template>
        </nav>
      </aside>

      <!-- 右侧内容区 -->
      <main class="flex-1 ml-64 p-6">
        <!-- 数据概览卡片 -->
        <div class="grid grid-cols-4 gap-6 mb-6">
          <template v-for="(card, index) in overviewCards" :key="index">
            <div class="bg-white rounded-lg shadow-sm p-6">
              <div class="flex items-center justify-between">
                <div>
                  <p class="text-gray-500 text-sm">{{ card.label }}</p>
                  <p class="text-2xl font-semibold mt-2">{{ card.value }}</p>
                </div>
                <div :class="['p-3 rounded-full', card.bgColor]">
                  <i :class="['fas', card.icon, card.textColor]"></i>
                </div>
              </div>
              <div class="mt-4 flex items-center">
                <span :class="card.trend === 'up' ? 'text-green-500' : 'text-red-500'">
                  <i :class="['fas', card.trend === 'up' ? 'fa-arrow-up' : 'fa-arrow-down']"></i>
                  {{ card.percentage }}%
                </span>
                <span class="text-gray-500 text-sm ml-2">较上周</span>
              </div>
            </div>
          </template>
        </div>

        <!-- 图表区域 -->
        <div class="grid grid-cols-2 gap-6 mb-6">
          <div class="bg-white rounded-lg shadow-sm p-6">
            <h3 class="text-lg font-medium mb-4">用户增长趋势</h3>
            <div ref="userTrendChart" class="h-80"></div>
          </div>
          <div class="bg-white rounded-lg shadow-sm p-6">
            <h3 class="text-lg font-medium mb-4">活跃度分析</h3>
            <div ref="activityChart" class="h-80"></div>
          </div>
        </div>

        <!-- 用户列表 -->
        <div class="bg-white rounded-lg shadow-sm p-6">
          <div class="flex justify-between items-center mb-6">
            <h3 class="text-lg font-medium">用户列表</h3>
            <div class="flex items-center space-x-4">
              <div class="relative">
                <input
                  type="text"
                  placeholder="搜索用户"
                  class="pl-10 pr-4 py-2 border rounded-lg focus:outline-none focus:border-blue-500"
                />
                <i class="fas fa-search absolute left-3 top-1/2 -translate-y-1/2 text-gray-400"></i>
              </div>
              <button class="!rounded-button bg-blue-600 text-white px-4 py-2 hover:bg-blue-700">
                添加用户
              </button>
            </div>
          </div>
          <table class="w-full">
            <thead>
              <tr class="bg-gray-50">
                <th class="px-4 py-3 text-left text-sm font-medium text-gray-500">用户名</th>
                <th class="px-4 py-3 text-left text-sm font-medium text-gray-500">注册时间</th>
                <th class="px-4 py-3 text-left text-sm font-medium text-gray-500">状态</th>
                <th class="px-4 py-3 text-left text-sm font-medium text-gray-500">操作</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(user, index) in users" :key="index" class="border-t">
                <td class="px-4 py-4">
                  <div class="flex items-center">
                    <img :src="user.avatar" class="w-8 h-8 rounded-full" />
                    <span class="ml-3">{{ user.name }}</span>
                  </div>
                </td>
                <td class="px-4 py-4 text-sm text-gray-500">{{ user.registerDate }}</td>
                <td class="px-4 py-4">
                  <span :class="[
                    'px-2 py-1 text-xs rounded-full',
                    user.status === '活跃' ? 'bg-green-100 text-green-600' : 'bg-gray-100 text-gray-600'
                  ]">
                    {{ user.status }}
                  </span>
                </td>
                <td class="px-4 py-4">
                  <button class="!rounded-button text-blue-600 hover:text-blue-700 mr-3">
                    <i class="fas fa-edit"></i>
                  </button>
                  <button class="!rounded-button text-red-600 hover:text-red-700">
                    <i class="fas fa-trash"></i>
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </main>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import * as echarts from 'echarts'

const avatarUrl = 'https://zhangyunpeng.mastergo.com/ai/api/search-image?flag=961c4f0c-f12d-40ec-948a-af28fe52af11'

const activeMenu = ref('overview')

const menuItems = [
  { key: 'overview', label: '数据概览', icon: 'fa-chart-pie' },
  { key: 'users', label: '用户管理', icon: 'fa-users' },
  { key: 'analytics', label: '统计分析', icon: 'fa-chart-line' },
  { key: 'settings', label: '系统设置', icon: 'fa-cog' },
  { key: 'permissions', label: '权限管理', icon: 'fa-lock' }
]

const overviewCards = [
  {
    label: '总用户数',
    value: '24,589',
    icon: 'fa-users',
    bgColor: 'bg-blue-50',
    textColor: 'text-blue-600',
    trend: 'up',
    percentage: 12
  },
  {
    label: '活跃用户',
    value: '12,825',
    icon: 'fa-user-check',
    bgColor: 'bg-green-50',
    textColor: 'text-green-600',
    trend: 'up',
    percentage: 8
  },
  {
    label: '日增长率',
    value: '2.5%',
    icon: 'fa-chart-line',
    bgColor: 'bg-yellow-50',
    textColor: 'text-yellow-600',
    trend: 'down',
    percentage: 3
  },
  {
    label: '转化率',
    value: '42%',
    icon: 'fa-exchange-alt',
    bgColor: 'bg-purple-50',
    textColor: 'text-purple-600',
    trend: 'up',
    percentage: 5
  }
]

const users = [
  {
    name: '陈志远',
    avatar: 'https://zhangyunpeng.mastergo.com/ai/api/search-image?flag=27053e98-d449-4051-8127-a5ee8bc88d1a',
    registerDate: '2023-12-01',
    status: '活跃'
  },
  {
    name: '林美玲',
    avatar: 'https://zhangyunpeng.mastergo.com/ai/api/search-image?flag=20aa7e30-4c1c-4e9f-8d82-cb45d3a6993e',
    registerDate: '2023-11-28',
    status: '离线'
  },
  {
    name: '王建国',
    avatar: 'https://zhangyunpeng.mastergo.com/ai/api/search-image?flag=0f2cfbcf-010e-4016-b9f3-6dfa0050931f',
    registerDate: '2023-11-25',
    status: '活跃'
  }
]

const userTrendChart = ref<HTMLElement | null>(null)
const activityChart = ref<HTMLElement | null>(null)

onMounted(() => {
  if (userTrendChart.value) {
    const chart = echarts.init(userTrendChart.value)
    chart.setOption({
      tooltip: {
        trigger: 'axis'
      },
      xAxis: {
        type: 'category',
        data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
      },
      yAxis: {
        type: 'value'
      },
      series: [{
        data: [820, 932, 901, 934, 1290, 1330, 1320],
        type: 'line',
        smooth: true
      }]
    })
  }

  if (activityChart.value) {
    const chart = echarts.init(activityChart.value)
    chart.setOption({
      tooltip: {
        trigger: 'item'
      },
      series: [{
        type: 'pie',
        radius: ['40%', '70%'],
        data: [
          { value: 1048, name: '日活用户' },
          { value: 735, name: '周活用户' },
          { value: 580, name: '月活用户' },
          { value: 484, name: '季活用户' }
        ]
      }]
    })
  }
})
</script>

<style scoped>
/* 移除number input的箭头 */
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>

