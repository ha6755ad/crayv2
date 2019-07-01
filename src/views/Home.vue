<template>
  <div class="home">
    <ProductMain/>
  </div>
</template>

<script>
// @ is an alias to /src
import ProductMain from "@/components/ProductMain.vue";

export default {
  name: "home",
  components: {
    ProductMain
  }
};
</script>
