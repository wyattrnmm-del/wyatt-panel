<script setup lang="ts">
import { NDivider, NGradientText } from 'naive-ui'
import srcSvglogo from '@/assets/logo.svg'
import srcGithub from '@/assets/about_image/github.png'
import srcTelegram from '@/assets/about_image/telegram.svg'
import srcMarket from '@/assets/about_image/market.svg'

const versionName = '2.04'
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
          <a href="https://github.com/liandu2024/AnGe-Panel/releases" class="font-semibold" :title="$t('apps.about.viewUpdateLog')" target="_blank">Ver: {{ versionName }}</a>
        </NGradientText>
      </div>
      <div class="mt-2">
        <a href="https://github.com/liandu2024/AnGe-Panel/releases" target="_blank" class="link">{{ $t('apps.about.checkUpdate') }}</a>
      </div>
    </div>

    <NDivider style="margin:10px 0">
      •
    </NDivider>
    <div class="flex flex-col items-center justify-center text-base">
      <div class="flex mt-[10px] flex-wrap justify-center">
        <div class="flex items-center mx-[10px]">
          <img class="w-[20px] h-[20px] mr-[5px]" :src="srcGithub" alt="">
          <a href="https://github.com/liandu2024/AnGe-Panel" target="_blank" class="link">Github</a>
        </div>
        <div class="flex items-center mx-[10px]">
          <img class="w-[20px] h-[20px] mr-[5px]" :src="srcTelegram" alt="">
          <a href="https://t.me/angeworld2024" target="_blank" class="link">安格视界TG群</a>
        </div>
        <div class="flex items-center mx-[10px]">
          <img class="w-[20px] h-[20px] mr-[5px]" :src="srcMarket" alt="">
          <a href="https://blog.angeworld.cc/market" target="_blank" class="link">安格超市</a>
        </div>
      </div>

      <div class="mt-5 flex flex-wrap justify-center gap-3">
        <a
          href="https://ai.superdoor.top"
          target="_blank"
          rel="noopener noreferrer"
          class="ai-link-button ai-link-button-primary"
        >
          SUPERDOOR（订阅制AI接口）
        </a>
        <a
          href="https://ai.opendoor.sbs"
          target="_blank"
          rel="noopener noreferrer"
          class="ai-link-button ai-link-button-info"
        >
          OPENDOOR（按需付费AI接口）
        </a>
      </div>

      <div class="mt-4 text-sm text-gray-500">
        <a href="https://github.com/hslr-s/sun-panel" target="_blank" class="link">本项目基于 Sun-Panel 开源版 v1.3.0 二次开发</a>
      </div>
    </div>
  </div>
</template>

<style>
.link{
    color:rgb(0, 89, 255)
}

.ai-link-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-height: 34px;
    padding: 0 14px;
    border-radius: 8px;
    border: 1px solid transparent;
    font-size: 14px;
    font-weight: 600;
    text-decoration: none;
    transition: background-color .2s ease, border-color .2s ease, color .2s ease;
}

.ai-link-button-primary {
    color: #0f5132;
    background-color: rgba(24, 160, 88, .14);
    border-color: rgba(24, 160, 88, .28);
}

.ai-link-button-primary:hover {
    color: #0a3d26;
    background-color: rgba(24, 160, 88, .22);
}

.ai-link-button-info {
    color: #12446f;
    background-color: rgba(32, 128, 240, .14);
    border-color: rgba(32, 128, 240, .28);
}

.ai-link-button-info:hover {
    color: #0b3154;
    background-color: rgba(32, 128, 240, .22);
}

.dark .ai-link-button-primary {
    color: #d1fae5 !important;
}

.dark .ai-link-button-info {
    color: #dbeafe !important;
}
</style>
