<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { useRegisterSW } from 'virtual:pwa-register/vue'

const { messages, locale } = useI18n()

const intervalMS = 60 * 60 * 1000

useRegisterSW({
  onRegistered(r) {
    r &&
      setInterval(() => {
        r.update()
      }, intervalMS)
  }
})
</script>

<template>
  <el-config-provider :locale="messages[locale] as any">
    <router-view />
  </el-config-provider>
</template>

<style scoped></style>
