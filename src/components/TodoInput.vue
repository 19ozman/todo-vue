<template>
  <div>
    <form @submit.prevent="createTodo">
      <input
        type="text"
        :placeholder="errormsg ? errormsg : `let's do something`"
        class="the-input"
        v-model="wtdInput"
      />
    </form>
  </div>
</template>

<script lang="ts">
import { Todo } from "@/models/Todo";
import { Options, Vue } from "vue-class-component";

@Options({
  watch: {
    todos: {
      handler() {
        localStorage.setItem("todo_items", JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
})
export default class TodoInput extends Vue {
  todos: Todo[] = [];
  wtdInput = "";
  errormsg = "";

  mounted() {
    this.todos = JSON.parse(localStorage.getItem("todo_items") || "[]");
  }

  createTodo(): void {
    let aId = "_id" + new Date().getTime();
    if (this.wtdInput === "") {
      this.errormsg = "You really gots' to do something!";
    } else {
      this.$emit("todoinput", new Todo(this.wtdInput, false, new Date(), aId));
      this.wtdInput = "";
    }

    console.log(this.wtdInput);
  }
}
</script>

<style scoped lang="scss">
div {
  display: flex;
  justify-content: center;
}

form {
  margin: 0;
}

.the-input {
  padding: 2rem;
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--black);
  border: none;
  background-color: var(--white);
  border-top-left-radius: 1rem;
  border-top-right-radius: 1rem;
  outline-style: none;
  width: 95vw;
  border-bottom: 0.05em solid var(--black);

  &::placeholder {
    text-align: center;
    font-weight: 600;
    text-transform: capitalize;
  }

  &:focus {
    outline-style: none;
  }
}

@media (min-width: 768px) {
  .the-input {
    width: 80vw;
  }
}

@media (min-width: 1024px) {
  .the-input {
    width: 45vw;
  }
}

@media (min-width: 1440px) {
  .the-input {
    width: 45vw;
  }
}
</style>
