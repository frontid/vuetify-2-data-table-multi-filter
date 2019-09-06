<template>
  <v-app>
    <v-content>
      <FilterAtColumn />
    </v-content>
  </v-app>
</template>

<script>
import FilterAtColumn from './components/filter-at-column/filter-at-column.vue';

export default {
  name: 'App',
  components: {
    FilterAtColumn,
  },
  data: () => ({
    //
  }),
};
</script>
