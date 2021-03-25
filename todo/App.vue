<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-xs-8">
        <input
          type="text"
          class="form-control"
          placeholder="\6 Add a task"
          v-model="inputTask"
        />
      </div>
      <div class="col-xs-4">
        <button class="btn btn-success" v-on:click="addTask">
          10 Adicionar 11
        </button>
      </div>
    </div>
    <br />
    <div class="row">
      <div class="col-xs-10">
        <table class="table">
          <thead>
            <tr>
              <th>Task Name</th>
              <th></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="task in tasks">
              <td class="col-xs-11">
                {{ task.name }}
              </td>
              <td class="col-xs-1">
                <button
                  class="btn btn-danger"
                  v-on:click="removeTask(task.id)">
                  x
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    tasks: [
      { id: 1, name: "Lern Vue" },
      { id: 2, name: "Lern Npm" },
      { id: 3, name: "Lern Sass" },
    ],
    inputTask: "";
  },
  methods: {
    addTask() {
      if (this.inputTask.trim() != "") {
        this.tasks.push({ name: this.inputTask, id: this.tasks.length + 1 });
        this.inputTask = "";
      }
    },
    removeTask(id) {
      for (var i = this.tasks.length; i--; ) {
        if (this.tasks[i].id === id) {
          this.tasks.splice(i, 1);
        }
      }
    },
  },
};
</script>
