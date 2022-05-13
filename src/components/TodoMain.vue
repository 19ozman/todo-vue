<template>
  <div>
    <TodoInputB v-if="todos.length === 0" @todoinput="pushTodo($event)" />
    <TodoInput v-else @todoinput="pushTodo($event)" />
  </div>
  <div class="todo-wrap">
    <div class="bb" v-for="todo in todos" :key="todo.id">
      <div class="span-wrap">
        <span
          :class="[{ dashed: todo.done }, nodash]"
          @click="toggleCmp(todo.id)"
          >{{ todo.wtd }}</span
        >
      </div>
      <div class="btn-wrap">
        <button class="delbtn" @click="delTodo(todo.id)"></button>
        <button class="edbtn" @click="showModal(todo.id)"></button>
      </div>
    </div>
  </div>
  <EditModal
    v-if="isModalVisible"
    :thisTodo="this.currentEdit"
    @close="closeModal"
  />
</template>

<script lang="ts">
import { Todo } from "@/models/Todo";
import { Options, Vue } from "vue-class-component";
import TodoInput from "./TodoInput.vue";
import TodoInputB from "./TodoInputB.vue";
import EditModal from "./EditModal.vue";

@Options({
  components: {
    TodoInput,
    TodoInputB,
    EditModal,
  },
  watch: {
    todos: {
      handler() {
        localStorage.setItem("todo_items", JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
})
export default class TodoMain extends Vue {
  todos: Todo[] = [];
  nodash = "nodash";
  isModalVisible = false;
  currentEdit: Todo | undefined = undefined;

  mounted() {
    this.todos = JSON.parse(localStorage.getItem("todo_items") || "[]");
  }

  showModal(id: string) {
    this.currentEdit = this.todos.find((obj) => obj.id === id);
    this.isModalVisible = true;
  }

  closeModal(id: string) {
    if ((this.currentEdit = this.todos.find((obj) => obj.id === id))) {
    }

    this.isModalVisible = !this.isModalVisible;
  }

  pushTodo(t: Todo) {
    this.todos.push(t);
  }

  delTodo(itemID: string) {
    this.todos = this.todos.filter((object) => {
      location.reload();
      return object.id !== itemID;
    });
  }

  toggleCmp(findID: string) {
    const todo = this.todos.find((obj) => obj.id === findID);
    if (todo) {
      todo.done = !todo.done;
    }
  }

  // sortTodo(sort: Date) {
  //   this.todos.sort(function (a, b) {
  //     let dateA = new Date(sort).getTime();
  //     let dateB = new Date(sort).getTime();
  //     return dateA < dateB ? 1 : -1; // ? -1 : 1 for ascending/increasing order
  //   });
  // }
}
</script>

<style scoped lang="scss">
.todo-wrap {
  display: flex;
  flex-direction: column;
  height: 57.6vh;
  border-bottom-left-radius: 3em;
  border-bottom-right-radius: 3em;
  overflow: scroll;
}

.bb {
  display: flex;
  flex-direction: row;
  width: 95vw;
  padding: 2rem;
  background-color: var(--white);
  border-bottom: 0.05rem solid var(--black);

  &:last-child {
    border-bottom-left-radius: 1rem;
    border-bottom-right-radius: 1rem;
  }
}

.span-wrap {
  width: 70vw;
  background-color: var(--white);
}

.btn-wrap {
  display: flex;
  justify-content: space-evenly;
  background-color: var(--white);
  min-width: 15vw;
  align-items: center;
  margin-left: 0.4vw;
}

.dashed {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--black);
  background-color: var(--white);
  text-decoration: line-through 0.3em var(--agreen);
  cursor: pointer;
}

.nodash {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--black);
  background-color: var(--white);
  cursor: pointer;
}

.delbtn {
  padding: 0;
  border: none;
  outline-style: none;
  background-color: var(--ared);
  border-radius: 50%;
  height: 1.5rem;
  width: 1.5rem;
  cursor: pointer;
}

.delbtn:hover {
  border: 0.1em solid var(--white);
  opacity: 0.7;
}

.edbtn {
  padding: 0;
  border: none;
  outline-style: none;
  background-color: var(--ayellow);
  border-radius: 50%;
  height: 1.5rem;
  width: 1.5rem;
  cursor: pointer;
}

.edbtn:hover {
  border: 0.1em solid var(--white);
  opacity: 0.7;
}

@media (min-width: 768px) {
  .bb {
    width: 80vw;
  }
  .btn-wrap {
    min-width: 7.5vw;
  }
}

@media (min-width: 1024px) {
  .bb {
    width: 45vw;
  }
  .btn-wrap {
    min-width: 5.5vw;
  }
}

@media (min-width: 1440px) {
  .bb {
    width: 45vw;
  }
  .btn-wrap {
    min-width: 3.5vw;
  }
}
</style>
