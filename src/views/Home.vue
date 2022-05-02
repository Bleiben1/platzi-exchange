<template>
  <div>
    <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100" />
    <px-assets-table v-if="!isLoading" :assets="assets" />
  </div>
</template>

<script>
import PxAssetsTable from '@/components/PxAssetsTable.vue'
import api from '@/api'

export default {
  name: '',
  components: {
    PxAssetsTable,
  },
  data() {
    return {
      assets: [],
      isLoading: true,
    }
  },
  created() {
    api
      .getAssets()
      .then((response) => (this.assets = response))
      .finally(() => (this.isLoading = false))
  },
}
</script>
