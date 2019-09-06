<template>
    <div>
        <v-data-table
                :headers="headers"
                :items="desserts"
                item-key="name"
                class="elevation-1"
                :search="search"
                :custom-filter="filterOnlyCapsText"
        >
            <template v-slot:top>
                <v-text-field v-model="search" label="Search (UPPER CASE ONLY)" class="mx-4"></v-text-field>
            </template>

        </v-data-table>
    </div>
</template>

<script>
  import tableData from './sampleDataTable';

  export default {
    data() {
      return {
        search: '',
        calories: '',
        desserts: tableData.data,
      }
    },
    computed: {
      headers() {
        return [
          {
            text: 'Dessert (100g serving)',
            align: 'left',
            sortable: false,
            value: 'name',
          },
          {
            text: 'Calories',
            value: 'calories',
          },
          {text: 'Fat (g)', value: 'fat'},
          {text: 'Carbs (g)', value: 'carbs'},
          {text: 'Protein (g)', value: 'protein'},
          {text: 'Iron (%)', value: 'iron'},
        ]
      },
    },
    methods: {
      filterOnlyCapsText(value, search, item) {
        return value != null &&
          search != null &&
          typeof value === 'string' &&
          value.toString().toLocaleUpperCase().indexOf(search) !== -1
      },
    },
  }
</script>
