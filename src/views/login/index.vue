<script setup lang="ts">
import { NButton, NCard, NForm, NFormItem, NGradientText, NInput, NSelect, useMessage } from 'naive-ui'
import { ref } from 'vue'
import { login } from '@/api'
import { useAppStore, useAuthStore } from '@/store'
import { SvgIcon } from '@/components/common'
import { router } from '@/router'
import { t } from '@/locales'
import { languageOptions } from '@/utils/defaultData'
import type { Language } from '@/store/modules/app/helper'

// const userStore = useUserStore()
const authStore = useAuthStore()
const appStore = useAppStore()
const ms = useMessage()
const loading = ref(false)
const languageValue = ref<Language>(appStore.language)

// const isShowCaptcha = ref<boolean>(false)
// const isShowRegister = ref<boolean>(false)

const form = ref<Login.LoginReqest>({
  username: '',
  password: '',
})

const loginPost = async () => {
  loading.value = true
  try {
    const res = await login<Login.LoginResponse>(form.value)
    if (res.code === 0) {
      authStore.setToken(res.data.token)
      authStore.setUserInfo(res.data)

      setTimeout(() => {
        ms.success(`Hi ${res.data.name},${t('login.welcomeMessage')}`)
        loading.value = false
        router.push({ path: '/' })
      }, 500)
    }
    else {
      loading.value = false
      // captchaRef.value.refresh()
    }
  }
  catch (error) {
    loading.value = false
    // 请检查网络或者服务器错误
    console.log(error)
  }
}

function handleSubmit() {
  // 点击登录按钮触发
  loginPost()
}

function handleChangeLanuage(value: Language) {
  languageValue.value = value
  appStore.setLanguage(value)
}
</script>

<template>
  <div class="login-container">
    <NCard class="login-card" style="border-radius: 20px;">
      <div class="mb-5 flex items-center justify-end">
        <div class="mr-2">
          <SvgIcon icon="ion-language" style="width: 20;height: 20;" />
        </div>
        <div class="min-w-[100px]">
          <NSelect v-model:value="languageValue" class="login-select" size="small" :options="languageOptions" @update-value="handleChangeLanuage" />
        </div>
      </div>

      <div class="login-title  ">
        <NGradientText :size="30" type="success" class="!font-bold">
          {{ $t('common.appName') }}
        </NGradientText>
      </div>
      <NForm :model="form" label-width="100px" @keydown.enter="handleSubmit">
        <NFormItem>
          <NInput v-model:value="form.username" class="login-input" :placeholder="$t('login.usernamePlaceholder')">
            <template #prefix>
              <SvgIcon icon="ph:user-bold" />
            </template>
          </NInput>
        </NFormItem>

        <NFormItem>
          <NInput v-model:value="form.password" class="login-input" type="password" :placeholder="$t('login.passwordPlaceholder')">
            <template #prefix>
              <SvgIcon icon="mdi:password-outline" />
            </template>
          </NInput>
        </NFormItem>

        <!-- <NFormItem v-if="isShowCaptcha">
          <div class="w-[120px] h-[34px] mr-[20px] rounded border flex cursor-pointer">
            <Captcha ref="captchaRef" src="/api/captcha/getImage" />
          </div>
          <NInput v-model:value="form.vcode" type="text" placeholder="请输入图像验证码" />
        </NFormItem> -->
        <NFormItem style="margin-top: 10px">
          <NButton class="login-submit" type="primary" block :loading="loading" @click="handleSubmit">
            {{ $t('login.loginButton') }}
          </NButton>
        </NFormItem>

        <!-- <div class="flex justify-end">
          <NButton v-if="isShowRegister" quaternary type="info" class="flex" @click="$router.push({ path: '/register' })">
            注册
          </NButton>
          <NButton quaternary type="info" class="flex" @click="$router.push({ path: '/resetPassword' })">
            忘记密码?
          </NButton>
        </div> -->

        <div class="login-powered flex justify-center">
          Powered By <a href="https://github.com/liandu2024/AnGe-Panel" target="_blank" class="login-powered-link ml-[5px]">Wyatt-Panel</a>
        </div>
      </NForm>
    </NCard>
  </div>
</template>

  <style>
    .login-container {
        padding: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background-color: #e6edf9;
    }

    /* 夜间模式 */
    .dark .login-container{
      background-color: rgb(43, 43, 43);
    }

    @media (min-width: 600px) {
        .login-card {
            width: auto;
            margin: 0px 10px;
        }
        .login-button {
            width: 100%;
        }
    }

    .login-card {
        margin: 20px;
        width: 100%;
        max-width: 360px;
        min-width: 0;
        border: 1px solid #c7d0dc !important;
        outline: none;
        background-color: rgba(255, 255, 255, 0.96);
        box-shadow: none !important;
    }

    @media (min-width: 600px) {
      .login-card {
        max-width: 420px;
      }
    }

  .login-title{
    text-align: center;
    margin: 20px;
  }

  .login-input,
  .login-submit,
  .login-select {
    --n-border-radius: 10px !important;
  }

  .login-card .n-input .n-input-wrapper,
  .login-card .n-button,
  .login-card .n-base-selection .n-base-selection-label {
    border-radius: 10px !important;
  }

  .login-powered {
    color: #64748b;
  }

  .login-powered-link {
    color: #475569;
  }

  .dark .login-card {
    color: #1f2937;
    background-color: rgba(255, 255, 255, 0.96) !important;
    border-color: #c7d0dc !important;
  }

  .dark .login-card .n-input,
  .dark .login-card .n-base-selection {
    --n-color: #ffffff !important;
    --n-color-focus: #ffffff !important;
    --n-color-active: #ffffff !important;
    --n-text-color: #111827 !important;
    --n-placeholder-color: #64748b !important;
    --n-icon-color: #64748b !important;
    --n-border: 1px solid #cbd5e1 !important;
    --n-border-hover: 1px solid #7dd3fc !important;
    --n-border-focus: 1px solid #34d399 !important;
    --n-border-active: 1px solid #34d399 !important;
    --n-caret-color: #10b981 !important;
    --n-box-shadow-focus: 0 0 0 2px rgba(52, 211, 153, 0.16) !important;
  }

  .dark .login-card .n-input-wrapper,
  .dark .login-card .n-input__input-el,
  .dark .login-card .n-base-selection-label {
    color: #111827 !important;
    background-color: #ffffff !important;
  }

  .dark .login-card .n-input__placeholder,
  .dark .login-card .n-base-selection-placeholder,
  .dark .login-card .n-input__input-el::placeholder {
    color: #64748b !important;
    opacity: 1 !important;
  }

  .dark .login-card .svg-icon,
  .dark .login-card .n-base-suffix,
  .dark .login-card .n-base-selection-label__render-label {
    color: #64748b !important;
  }

  .dark .login-card .login-submit .n-button__content {
    color: #0f172a !important;
  }
  </style>
