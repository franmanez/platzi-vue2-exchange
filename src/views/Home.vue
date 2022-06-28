<template>
  <div>
    <!--bounce-louder :loading="isLoading" :color="'#68d391'" :size="100" /-->
    <px-assets-table :assets="assets" />
  </div>
</template>

<script>
import api from "@/api";
import PxAssetsTable from "@/components/PxAssetsTable";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  components: { PxAssetsTable },

  data() {
    return {
      isLoading: false,
      assets: [],
    };
  },

  created() {
    this.isLoading = true;
    api
      .getAssets()
      .then((assets) => (this.assets = assets))
      .finally(() => (this.isLoading = false));
  },
};
</script>
