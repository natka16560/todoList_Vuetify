<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col>
          <v-text-field
            v-model="newTask"
            label="Новая задача"
            @keyup.enter="addTask"
          ></v-text-field>
          <v-btn @click="addTask">Добавить задачу</v-btn>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <v-list>
            <v-list-item
              v-for="(task, index) in tasks"
              :key="index"
            >
              <v-list-item-content>{{ task }}</v-list-item-content>
              <v-list-item-action>
                <v-btn icon @click="removeTask(index)">
                  <v-icon>mdi-delete</v-icon>
                </v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-list>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push(this.newTask);
        this.newTask = "";
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>

</style>
