<template>
  <div class="bg-white shadow rounded px-3 pt-3 pb-5 border border-white">
    <div class="flex justify-between">
      <p class="text-gray-700 font-semibold font-sans tracking-wide text-sm">{{ task.title }}</p>
      <img
          class="w-6 h-6 rounded-full ml-3"
          :src="task.avatar"
      >
    </div>
    <div class="flex mt-1 justify-between items-center">
      <span class="text-xs text-gray-600">{{ task.create_date }}</span>
      <badge color="yellow">{{task.cliente}} - {{task.solicitante}}</badge>
    </div>
    <div class="flex mt-1 justify-between items-center">
      <span class="text-xs text-gray-600">{{ task.due_date }}</span>
      <badge v-if="task.type" :color="badgeColor">{{ task.type }}</badge>
    </div>
    <v-icon>mdi-plus</v-icon>
    <div class="flex mt-4 rounded-sm shadow">
      <a href="#" class="inline-flex items-center justify-center px-3 py-1 border border-transparent text-base font-small text-indigo-600 bg-white ">
        + Detalhes
      </a>
    </div>

  </div>
</template>
<script>
import Badge from "./Badge.vue";

export default {
  components: {
    Badge
  },
  props: {
    task: {
      type: Object,
      default: () => ({})
    }
  },
  computed: {
    badgeColor() {
      const mappings = {
        Design: "purple",
        "Feature Request": "teal",
        Backend: "blue",
        QA: "green",
        default: "teal"
      };
      return mappings[this.task.type] || mappings.default;
    }
  }
};
</script>
