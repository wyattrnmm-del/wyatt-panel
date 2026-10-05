<script setup lang="ts">
import { NDivider, NGradientText } from 'naive-ui'
import srcSvglogo from '@/assets/logo.svg'

const versionName = '2.04'
const wyattRepository = 'https://github.com/wyattrnmm-del/wyatt-panel'
</script>

<template>
  <div class="pt-5">
    <div class="flex flex-col items-center justify-center">
      <img :src="srcSvglogo" width="100" height="100" alt="">
      <div class="text-3xl font-semibold">
        Wyatt-Panel
      </div>
      <div class="text-xl">
        <NGradientText type="info">
          <a :href="wyattRepository" class="font-semibold" :title="$t('apps.about.viewUpdateLog')" target="_blank">Ver: {{ versionName }}</a>
        </NGradientText>
      </div>
      <div class="mt-2">
        <a :href="wyattRepository" target="_blank" class="link">{{ $t('apps.about.checkUpdate') }}</a>
      </div>
    </div>

    <NDivider style="margin:10px 0">
      •
    </NDivider>
    <div class="flex flex-col items-center justify-center text-base">
      <div class="mt-5 text-center text-sm text-gray-500">
        Wyatt-Panel：简洁、可靠、可自托管的家庭服务面板
      </div>

      <div class="mt-4 text-sm text-gray-500">
        <span>基于 Sun-Panel 开源版 v1.3.0 二次开发，遵循 MIT License</span>
      </div>
    </div>
  </div>
</template>

<style>
.link{
    color:rgb(0, 89, 255)
}


</style>
