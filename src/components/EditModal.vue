<template>
  <div class="modal-backdrop">
    <div class="modal">
      <div class="modal-wrap">
        <textarea class="edit-todo" v-model="thisTodo.wtd"></textarea>
      </div>
      <div class="save-wrap">
        <button type="button" class="btn-close" @click="close"></button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Todo } from "@/models/Todo";
import { Vue } from "vue-class-component";
import { Prop } from "vue-property-decorator";

export default class EditModal extends Vue {
  @Prop() thisTodo!: Todo;

  close() {
    this.$emit("close");
  }
}
</script>

<style scoped lang="scss">
.modal-backdrop {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
}

.modal {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--white);
  border-radius: 1rem;
  overflow: scroll;
  height: 15vh;
  width: 95vw;
  overflow-y: auto;
  overflow: -moz-scrollbars-none;
  -ms-overflow-style: none;
  &::-webkit-scrollbar {
    width: 0 !important;
  }
}

.modal-wrap {
  display: flex;
  align-items: center;
  height: 12vh;
  background-color: var(--white);
  margin: 0;
  overflow-y: auto;
  overflow: -moz-scrollbars-none;
  -ms-overflow-style: none;
  &::-webkit-scrollbar {
    width: 0 !important;
  }
}

.edit-todo {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 1.2rem;
  font-weight: 600;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--black);
  background-color: var(--white);
  width: 84vw;
  height: 12vh;
  resize: none;
  outline-style: none;
  border: none;
  overflow: scroll;
  margin: 0;
  margin-left: 2rem;
  overflow-y: auto;
  overflow: -moz-scrollbars-none;
  -ms-overflow-style: none;
  &::-webkit-scrollbar {
    width: 0 !important;
  }
}

.edit-todo:focus {
  outline-style: none;
}

.save-wrap {
  display: flex;
  align-items: flex-end;
  background-color: var(--white);
  height: 12vh;
  width: 5vw;
  margin: 0;
  scrollbar-width: none;
  overflow-y: auto;
  overflow: -moz-scrollbars-none;
  -ms-overflow-style: none;
  &::-webkit-scrollbar {
    width: 0 !important;
  }
}

.btn-close {
  padding: 0;
  border: none;
  outline-style: none;
  background-color: var(--agreen);
  border-radius: 50%;
  height: 1.5rem;
  width: 1.5rem;
  cursor: pointer;
}

.btn-close:hover {
  border: 0.1em solid var(--white);
  opacity: 0.7;
}

@media (min-width: 563px) and (max-width: 869px) {
  .modal {
    width: 45vw;
  }

  .edit-todo {
    width: 38vw;
  }
}

@media (min-width: 870px) and (max-width: 1023px) {
  .modal {
    width: 35vw;
  }

  .edit-todo {
    width: 28vw;
  }
}

@media (min-width: 1024px) and (max-width: 4400px) {
  .modal {
    width: 30vw;
  }

  .edit-todo {
    width: 26vw;
  }

  .save-wrap {
    justify-content: flex-end;
    padding-right: 1.2rem;
  }

  .btn-close {
    margin: 0;
  }
}
</style>
