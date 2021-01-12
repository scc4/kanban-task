<template>
  <div class="bg-white shadow rounded px-3 pt-3 pb-5 border border-white">
    <div class="flex justify-between">
      <p class="text-gray-700 font-semibold font-sans tracking-wide text-sm">{{ task.title }}</p>
      <img
          class="w-6 h-6 rounded-full ml-3"
          :src="task.avatar"
      >
    </div>
    <div class="flex mt-1 justify-between">
      <span class="text-xs text-gray-600">{{ task.create_date }}</span>
      <badge color="yellow">{{task.cliente}} - {{task.solicitante}}</badge>
    </div>
    <div class="flex mt-1 justify-between">
      <span class="text-xs  text-gray-600">{{ task.due_date }}</span>
      <badge v-if="task.type" :color="badgeColor">{{ task.type }}</badge>
    </div>
    <div>
      <v-btn
          class="mx-2"
          fab
          x-small
          color="accent"
          @click.stop="dialog = true"
      >
        <v-icon>
          mdi-dots-horizontal
        </v-icon>
      </v-btn>
      <v-dialog
          v-model="dialog"
          max-width="600"

      >
        <v-card>
          <v-card-title class="headline">
           {{task.id}} - {{task.title}}
          </v-card-title>
          <v-card-text>
            Let Google help apps determine location. This means sending anonymous location data to Google, even when no apps are running.
          </v-card-text>
          <v-card-text>
            Let Google help apps determine location. This means sending anonymous location data to Google, even when no apps are running.
          </v-card-text>
          <v-card-text>
            Let Google help apps determine location. This means sending anonymous location data to Google, even when no apps are running.
          </v-card-text>
          <v-card-text>
            Let Google help apps determine location. This means sending anonymous location data to Google, even when no apps are running.
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn
                color="green darken-1"
                text
                @click="dialog = false"
            >
              Fechar
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
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
  data () {
    return {
      dialog: false,
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
<style>
.flex, .child-flex > * {
  flex: none !important;
}
</style>
