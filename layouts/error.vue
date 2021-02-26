<template>
  <div class="nuxt-error">
    <section class="nuxt-error-content">
      <component :is="errorPage" :error="error"></component>
      <p class="nuxt-error-footer">
        <a href="#" class="text-primary" @click.prevent="$router.go(-1)"
          ><i class="el-icon-back"></i> Go back</a
        >
        <a href="/" class="text-secondary"><i class="el-icon-s-home"></i> Go home</a>
      </p>
    </section>
  </div>
</template>
<script>
import Error404 from '@/components/error/404'
import Error401 from '@/components/error/401'
import ErrorGeneral from '@/components/error/General'

export default {
  layout: 'empty',
  components: {
    Error404,
    Error401,
    ErrorGeneral,
  },
  props: {
    error: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {}
  },
  computed: {
    errorPage() {
      if (this.error.statusCode === 404) {
        return Error404
      } else if (this.error.statusCode === 401) {
        return Error401
      }
      return ErrorGeneral
    },
  },
}
</script>
<style lang="scss" scoped>
.nuxt-error {
  padding: 0;

  &-content {
    min-height: 100vh;
    margin-left: auto;
    margin-right: auto;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  &-footer {
    font-size: 18px;
    a {
      margin: 0 20px;
    }
  }

  &-desc {
    font-size: 22px;
    margin-bottom: 15px;
  }
}
</style>
