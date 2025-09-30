<script setup lang="ts">
import { useStorage } from '@vueuse/core'

definePageMeta({
  middleware: 'realtime-chat',
})

const { t } = useI18n()

// Persist setting in localStorage
const realtimeChatEnabled = useStorage<boolean>('realtimeChatEnabled', false)
</script>

<template>
  <div class="flex min-h-screen items-center justify-center">
    <div class="w-full max-w-md p-6">
      <ClientOnly>
        <h1
          class="mb-4 text-center text-2xl font-bold dark:text-gray-100"
        >
          {{ t('menu.realtime') }}
        </h1>

        <p
          v-if="realtimeChatEnabled"
          class="text-center text-gray-600 dark:text-gray-400"
        >
          Click the microphone indicator at the right edge of the page to start a
          voice conversation.
        </p>

        <p
          v-else
          class="text-center text-gray-600 dark:text-gray-400"
        >
          Please
          <NuxtLink
            to="/settings"
            class="text-primary hover:underline"
          >
            enable realtime chat in settings
          </NuxtLink>
          to start voice conversations.
        </p>
      </ClientOnly>
    </div>
  </div>
</template>
