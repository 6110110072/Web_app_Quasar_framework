<template>
  <q-page class="bg-gray-3 column">
    <div class="row q-pa-sm bg-pink">
      <q-input
        class="col"
        square
        bg-color="white"
        filled
        v-model="newTask"
        placeholder="Add Task"
        dense
      >
        <template v-slot:append>
          <q-btn
            @keyup.enter="addTask"
            @click="addTask"
            round
            dense
            flat
            icon="add"
          />
        </template>
      </q-input>
    </div>
    <q-list class="bg-white" separator bordered>
      <q-item
        v-ripple
        v-for="(task, index) in tasks"
        :key="task.title"
        @click="task.done = !task.done"
        :class="{ 'done bg-pink-2': task.done }"
        clickable
      >
        <q-item-section avatar>
          <q-checkbox
            class="no-pointer-events"
            color="primary"
            v-model="task.done"
            val="teal"
          />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn
            @click.stop="deleteTask(index)"
            flat
            dense
            round
            color="red"
            icon="delete"
          ></q-btn>
        </q-item-section>
      </q-item>

    </q-list>
    <div v-if="!tasks.length" class="no-tasks absolute-center" style="text-align:center;">
      <!-- <q-icon name= "check" size="100px" color="primary"></q-icon> -->
      

      <img src="../statics/shopping-cart.png" style="width:100px;height:100px" alt="">
      <div class="text-h5 text-primary text-cent">
        Today no tasks
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import { LocalStorage } from "quasar";

export default defineComponent({
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    deleteTask(index) {
      this.$q
        .dialog({
          title: "Confirm",
          message: "Would you like to delete ?",
          cancel: true,
          persistent: true,
        })
        .onOk(() => {
          this.tasks.splice(index, 1);
          this.$q.notify("Task deleted");
        });
    },
    addTask() {
      if (this.newTask) {
        this.tasks.push({
          title: this.newTask,
          done: false,
        });
        this.newTask = "";
      }
    },
  },
});
</script>

<style lang="scss">
.done {
  .q-item__label {
    text-decoration: line-through;
    color: #bbb;
  }
}
.no-tasks{
  opacity: 0.5;
}

.q-checkbox__bg{
border-radius: 10px !important;
}
</style>
