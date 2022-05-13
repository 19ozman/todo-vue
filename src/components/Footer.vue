<template>
  <div class="foot-wrap">
    <span class="foot-info">wtd?! - 2022</span>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class Footer extends Vue {}
</script>

<style scoped lang="scss">
.foot-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  min-height: 10vh;

  .foot-info {
    font-size: 1.2rem;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: 0.3rem;
    text-indent: 0.3rem;
    color: var(--white);
  }
}
</style>
