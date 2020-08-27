<template>
  <v-container id="todos">
    <section id="new-todo">
      <v-row>
        <v-col cols="12">
          <h4>Hy {{ name }}</h4>
          <br />
          <v-form ref="form" v-model="formValid">
            <v-col cols="12">
              <v-text-field
                v-model="todo.description"
                label="todo description"
                outlined
                :rules="[v => !!v || 'description is required']"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="3">
              <v-select
                v-model="todo.criticality"
                :items="criticalities"
                label="select a criticity"
                :rules="[v => !!v || 'criticity is required']"
                outlined
              ></v-select>
            </v-col>
            <v-col cols="12">
              <v-btn
                color="primary"
                outlined
                x-large
                :disabled="!formValid"
                @click="createTodo"
              >
                Create
              </v-btn>
            </v-col>
          </v-form>
        </v-col>
      </v-row>
      <v-divider></v-divider>
      
    </section>
  </v-container>
</template>
<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import Todo from "@/models/todo";
import { Criticality } from "@/config/enum/criticality";

@Component({})
export default class Todos extends Vue {
  private formValid = true;
  private name = "";
  private todo = new Todo();
  private todos: Todo[] = [];
  private criticalities = Object.keys(Criticality);

  public created() {
    this.name = this.$route.query.name as string;
  }

  private createTodo(): void {
      console.log(this.todo);
  }
}
</script>
