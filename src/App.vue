<template>
  <v-app>
    <v-content>
      <CustomFilterDatatableComponent></CustomFilterDatatableComponent>
    </v-content>
  </v-app>
</template>

<script>
import CustomFilterDatatableComponent from './components/custom-filter-datatable-component/custom-filter-datatable-component.vue';

export default {
  name: 'App',
  components: {
    CustomFilterDatatableComponent,
  },
  data: () => ({
    //
  }),
};
</script>
