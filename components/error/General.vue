<template>
  <div v-if="isDev" class="">
    <div style="max-width: 65%" class="text-left mx-auto code-block">
      <pre><code class="code-block">{{ error }}</code></pre>
    </div>
  </div>
  <div v-else class="nuxt-error-desc">ERROR | Something wrong</div>
</template>
<script>
export default {
  props: {
    error: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    isDev() {
      return process.env.NODE_ENV !== 'production'
    },
  },
}
</script>
