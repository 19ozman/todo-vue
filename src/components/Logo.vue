<template>
  <div class="title-cnt">
    <span class="title">wtd?!</span>
  </div>
  <div class="logo-cnt">
    <span class="descript">Click TODO to toggle complete ON/OFF</span>
    <span class="descript">• RED to REMOVE</span>
    <span class="descript">• YELLOW to EDIT</span>
    <span class="descript">• GREEN to SAVE</span>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class Logo extends Vue {}
</script>

<style scoped lang="scss">
.title-cnt {
  display: flex;
  width: 100vw;

  .title {
    text-align: center;
    font-size: 5rem;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: 2rem;
    text-indent: 2rem;
    color: var(--signal);
  }
}

.logo-cnt {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100vw;
  margin-bottom: 2rem;

  .descript {
    display: flex;
    align-items: center;
    text-align: center;
    font-weight: 900;
    font-size: 1rem;
    line-height: 1.9rem;
    color: var(--white);
    letter-spacing: 0.3rem;
    text-indent: 0.3rem;
  }
}

@media (min-width: 375px) {
  .title-cnt {
    .title {
      font-size: 7rem;
    }
  }
}

@media (min-width: 768px) {
  .logo-cnt {
    flex-direction: row;

    .descript {
      margin: 0;
    }
  }

  .title-cnt {
    .title {
      font-size: 10rem;
    }
  }
}
</style>
