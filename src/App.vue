<template>
  <el-config-provider :locale="locale">
    <div class="am-main">
      <div class="am-title">
        Armoe Project
      </div>
      <el-button v-for="project in projects" type="primary" @click="pushTo(project.url)">{{ project.name }}</el-button>
      <div class="am-footer">
        <div class="am-copyright">
          &copy;{{ currentYear }} <a href="https://github.com/armoe-project">Armoe Project</a> All Rights Reserved.
        </div>
        <div>
          <a href="https://beian.miit.gov.cn/">辽ICP备19016520号-3</a>
        </div>
      </div>
    </div>
  </el-config-provider>
</template>

<script lang="ts" setup>
import { onMounted, ref } from 'vue';
import { useDark, useToggle } from '@vueuse/core'
import locale from 'element-plus/es/locale/lang/zh-cn';

const projects = ref([
  {
    name: 'mihoyo-api',
    url: 'https://github.com/armoe-project/mihoyo-api'
  },
  {
    name: 'qqbot-sdk',
    url: 'https://github.com/armoe-project/qqbot-sdk'
  }
])

const pushTo = (url: string) => {
  location.href = url
}

const currentYear = new Date().getFullYear()

onMounted(() => {
  const isDark = useDark()
  useToggle(isDark)
})
</script>

<style lang="scss">
.am-main {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

.am-title {
  font-size: 25px;
  font-weight: bold;
  margin-bottom: 20%;
}

.am-footer {
  text-align: center;
  margin-top: 20%;
  font-size: 14px;

  a {
    text-decoration: none;
    color: var(--el-text-color-primary);
  }

  a:hover {
    text-decoration: underline;
  }
}

.am-copyright {
  margin-bottom: 10px;
}
</style>
