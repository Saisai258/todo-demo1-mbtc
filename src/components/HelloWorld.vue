<template>
  <v-container>
    <h2>{{ title }}</h2>

    <v-text-field label="Enter your name:" v-model="name" @keydown.enter="changeFlag" :disabled="flag"></v-text-field>

    <p>Hello: {{ name }}</p>

    <v-row>
      <v-col cols="9">
        <v-text-field label="What will you do" v-model="todo"></v-text-field>
      </v-col>
      <v-col cols="3">
        <v-text-field label="How long it will take" v-model="duration"></v-text-field>
      </v-col>
    </v-row>

    <div>
      <v-btn @click="add">Add To Do List</v-btn>
    </div>

    <div>
      <v-table>
        <thead>
          <tr>
            <th class="text-left">No.</th>
            <th class="text-left">TODO</th>
            <th class="text-left">Duration</th>
            <th class="text-left">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in todolist" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.todo }}</td>
            <td>{{ item.duration }} hr(s)</td>
            <td>
              <v-btn color="error" @click="deleteItem(item.id)" small>Delete</v-btn>
            </td>
          </tr>
        </tbody>
      </v-table>
    </div>
  </v-container>
</template>
<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    title: "This is my first vue project.",
    name: "",
    flag: false,
    todo: "",
    duration: "",
    todolist: [
      { id: 1, todo: 'OJT', duration: 3 },
      { id: 2, todo: 'clean the house', duration: 0.5 },
    ]
  }),

  methods: {
    add() {
      if (this.todo && this.duration > 0) {
        this.todolist.push({
          id: this.todolist.length > 0 ? Math.max(...this.todolist.map(t => t.id)) + 1 : 1,
          todo: this.todo,
          duration: this.duration
        });
        this.todo = "";
        this.duration = "";
      } else {
        alert("Please enter both task and duration!");
      }
    },
    deleteItem(id) {
      this.todolist = this.todolist.filter(item => item.id !== id);
    },
    changeFlag() {
      this.flag = !this.flag;
    }
  }
}
</script>
