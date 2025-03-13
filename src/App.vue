<!-- The exported code uses Tailwind CSS. Install Tailwind CSS in your dev environment to ensure all styles work. -->
<template>
    <div class="min-h-screen bg-white">
        <!-- 导航栏 -->
        <nav class="h-16 border-b border-gray-100 px-8 flex items-center justify-between">
            <div class="flex items-center">
                <img :src="logoUrl" alt="Logo" class="h-8 w-auto cursor-pointer" />
            </div>
            <div class="flex items-center space-x-4">
                <el-button class="!rounded-button whitespace-nowrap cursor-pointer" @click="showHistory">
                    <el-icon class="mr-1">
                        <Clock />
                    </el-icon>历史记录
                </el-button>
                <el-button class="!rounded-button whitespace-nowrap cursor-pointer" @click="showSettings">
                    <el-icon class="mr-1">
                        <Setting />
                    </el-icon>设置
                </el-button>
            </div>
        </nav>
        <!-- 主要内容区 -->
        <div class="flex flex-col items-center justify-center px-8 py-16">
            <div class="w-full max-w-3xl">
                <div class="relative group">
                    <div class="relative">
                        <el-input v-model="url" placeholder="请输入网址"
                            class="text-lg transition-transform duration-300 transform group-focus-within:scale-105"
                            :class="{'error-input': showError}" @keyup.enter="navigate" clearable>
                            <template #prefix>
                                <el-icon>
                                    <Search />
                                </el-icon>
                            </template>
                        </el-input>
                        <el-button type="primary"
                            class="!rounded-button whitespace-nowrap absolute right-0 top-0 h-full px-8"
                            @click="navigate">
                            前往
                        </el-button>
                    </div>
                    <div v-if="showError" class="text-red-500 mt-2">
                        请输入有效的网址
                    </div>
                </div>
                <!-- 快捷访问区 -->
                <div class="mt-12">
                    <h2 class="text-xl font-medium mb-6">常用网站</h2>
                    <div class="grid grid-cols-4 gap-6">
                        <div v-for="site in frequentSites" :key="site.id"
                            class="group cursor-pointer bg-gray-50 rounded-lg p-4 transition-all duration-300 hover:shadow-lg"
                            @click="visitSite(site.url)">
                            <div class="aspect-w-16 aspect-h-9 mb-3 overflow-hidden rounded-lg">
                                <img :src="site.thumbnail" :alt="site.name" class="w-full h-full object-cover" />
                            </div>
                            <h3 class="text-sm font-medium text-gray-900 group-hover:text-blue-600 truncate">
                                {{ site.name }}
                            </h3>
                            <p class="text-xs text-gray-500 mt-1 truncate">{{ site.url }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- 设置对话框 -->
        <el-dialog v-model="settingsVisible" title="设置" width="500px">
            <div class="p-4">
                <el-form label-width="100px">
                    <el-form-item label="搜索引擎">
                        <el-select v-model="settings.searchEngine" class="w-full">
                            <el-option label="百度" value="baidu" />
                            <el-option label="谷歌" value="google" />
                            <el-option label="必应" value="bing" />
                        </el-select>
                    </el-form-item>

                </el-form>
            </div>
        </el-dialog>
        <!-- 历史记录对话框 -->
        <el-dialog v-model="historyVisible" title="历史记录" width="800px">
            <el-table :data="historyRecords" style="width: 100%">
                <el-table-column prop="title" label="网站" />
                <el-table-column prop="url" label="网址" />
                <el-table-column prop="visitTime" label="访问时间" />
                <el-table-column fixed="right" label="操作" width="120">
                    <template #default="scope">
                        <el-button type="text" class="!rounded-button whitespace-nowrap cursor-pointer"
                            @click="visitSite(scope.row.url)">
                            访问
                        </el-button>
                    </template>
                </el-table-column>
            </el-table>
        </el-dialog>
    </div>
</template>
<script lang="ts" setup>
    import { ref } from 'vue';
    import { Clock, Setting, Search } from '@element-plus/icons-vue';
    const logoUrl = 'https://dev-public.readdy.ai/ai/img_res/5c0375478ec49ab5a17b10f6dffb51c0.jpg';
    const url = ref('');
    const showError = ref(false);
    const settingsVisible = ref(false);
    const historyVisible = ref(false);
    const settings = ref({
        searchEngine: 'baidu'
    });
    const frequentSites = ref([
        {
            id: 1,
            name: '淘宝网',
            url: 'https://www.taobao.com',
            thumbnail: 'https://dev-public.readdy.ai/ai/img_res/f8af8252d7d57f77833290f454384cb8.jpg'
        },
        {
            id: 2,
            name: '京东商城',
            url: 'https://www.jd.com',
            thumbnail: 'https://dev-public.readdy.ai/ai/img_res/c2bdf3623776a7fef7819b9492315d0d.jpg'
        },
        {
            id: 3,
            name: '哔哩哔哩',
            url: 'https://www.bilibili.com',
            thumbnail: 'https://dev-public.readdy.ai/ai/img_res/5888f7cf0cb0083db5cc65302fea8685.jpg'
        },
        {
            id: 4,
            name: '知乎',
            url: 'https://www.zhihu.com',
            thumbnail: 'https://dev-public.readdy.ai/ai/img_res/9e0c125188317b504aa2477cc2077aee.jpg'
        }
    ]);
    const historyRecords = ref([
        {
            title: '淘宝网 - 淘！我喜欢',
            url: 'https://www.taobao.com',
            visitTime: '2025-03-13 14:30'
        },
        {
            title: '京东(JD.COM) - 正品低价、品质保障',
            url: 'https://www.jd.com',
            visitTime: '2025-03-13 14:15'
        },
        {
            title: '哔哩哔哩 (゜-゜)つロ 干杯~',
            url: 'https://www.bilibili.com',
            visitTime: '2025-03-13 13:45'
        }
    ]);
    const navigate = () => {
        if (!url.value) {
            showError.value = true;
            return;
        }
        const urlPattern = /^(https?:\/\/)?([\da-z.-]+)\.([a-z.]{2,6})([/\w .-]*)*\/?$/;
        if (!urlPattern.test(url.value)) {
            showError.value = true;
            return;
        }
        showError.value = false;
        const fullUrl = url.value.startsWith('http') ? url.value : `https://${url.value}`;
        window.open(fullUrl, '_self');
    };
    const visitSite = (siteUrl: string) => {
        window.open(siteUrl, '_self');
    };
    const showSettings = () => {
        settingsVisible.value = true;
    };
    const showHistory = () => {
        historyVisible.value = true;
    };
</script>
<style scoped>
    .error-input :deep(.el-input__inner) {
        border-color: #ff4949;
    }

    .error-input :deep(.el-input__inner:focus) {
        border-color: #ff4949;
        box-shadow: 0 0 0 2px rgba(255, 73, 73, 0.2);
    }
</style>
