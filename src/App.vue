<template>
  <div id="app">
    <div class="flex justify-center">
      <div class="min-h-screen flex overflow-x-scroll py-12">
        <div
          v-for="column in columns"
          :key="column.title"
          class="bg-gray-100 rounded-lg px-3 py-3 column-width rounded mr-4"
        >
          <p class="text-gray-700 font-semibold font-sans tracking-wide text-sm">{{column.title}}</p>
          <!-- Draggable component comes from vuedraggable. It provides drag & drop functionality -->
          <draggable :list="column.tasks" :animation="200" ghost-class="ghost-card" group="tasks" :component-data="getComponentData()"">
            <!-- Each element from here will be draggable and animated. Note :key is very important here to be unique both for draggable and animations to be smooth & consistent. -->
            <task-card
              v-for="(task) in column.tasks"
              :key="task.id"
              :task="task"
              class="mt-3 cursor-move"
            ></task-card>
            <!-- </transition-group> -->
          </draggable>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import TaskCard from "./components/TaskCard.vue";
export default {
  name: "App",
  components: {
    TaskCard,
    draggable
  },
  data() {
    return {
      columns: [
        {
          title: "Backlog",
          tasks: [
            {
              id: 1,
              title: "Add discount code to checkout page",
              cliente: 'AGF Chapadão',
              solicitante: 'Carlos',
              due_date: "15/01/2021",
              create_date: "22/12/2020",
              avatar: 'https://scc4-floripa.s3.amazonaws.com/usuarios/avatar/thumbnail.1ae40db3-7d99-4a99-88de-6e8e30405ce5__SCC4__Cartoon%20Ricardo.PNG',
              type: "Solicitação"
            },
            {
              id: 2,
              title: "Provide documentation on integrations",
              cliente: 'AGF General Osorio',
              solicitante: 'Eder',
              due_date: "15/01/2021",
              create_date: "22/12/2020",
              avatar: 'https://scc4-floripa.s3.amazonaws.com/usuarios/avatar/thumbnail.3e7837bc-bffa-4a3c-b8c1-b76ca748ca41__SCC4__Cartoon%20Ismael.PNG',
              type: "Bug"
            },

          ]
        },
        {
          title: "Em Desenvolvimento",
          tasks: [
            {
              id: 6,
              title: "Design shopping cart dropdown",
              cliente: 'AGF Novo Mundo',
              solicitante: 'Bruno',
              due_date: "15/01/2021",
              create_date: "22/12/2020",
              avatar: 'https://scc4-floripa.s3.amazonaws.com/usuarios/avatar/thumbnail.80403e4d-b514-4a38-b6b8-7a9254e4fc3f__SCC4__Cartoon%20Fabio.PNG',
              type: "Evolutiva"
            }

          ]
        },
        {
          title: "Code Review",
          tasks: [

          ]
        },
        {
          title: "Finalizado",
          tasks: [

          ]
        }
      ]

    };
  },
  methods: {
    handleChange() {
      console.log('changed');
      console.log(this.columns[0]);
    },


    getComponentData() {
      return {
        on: {
          change: this.handleChange,
        }
      };
    }
  }
};
</script>

<style scoped>
.column-width {
  min-width: 320px;
  width: 320px;
}
/* Unfortunately @apply cannot be setup in codesandbox,
but you'd use "@apply border opacity-50 border-blue-500 bg-gray-200" here */
.ghost-card {
  opacity: 0.5;
  background: #F7FAFC;
  border: 1px solid #4299e1;
}
</style>
