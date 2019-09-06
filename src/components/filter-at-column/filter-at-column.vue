<template>

    <v-container>
        <v-row>
            <v-col cols="12">


                <v-data-table
                        :headers="headers"
                        :items="desserts"
                        item-key="name"
                        class="elevation-1 pa-6"
                >
                    <template v-slot:top>


                        <v-container fluid>
                            <v-row>

                                <v-col cols="6">
                                    <v-row class="pa-6">
                                        <!-- Filter for dessert name-->
                                        <v-text-field v-model="dessertFilterValue" type="text" label="Name"></v-text-field>
                                    </v-row>
                                </v-col>

                                <v-col cols="6">
                                    <v-row class="pa-6">
                                        <!-- Filter for calories -->
                                        <v-select
                                                :items="caloriesList"
                                                v-model="caloriesFilterValue"
                                                label="Calories"
                                        ></v-select>
                                    </v-row>
                                </v-col>

                            </v-row>
                        </v-container>

                    </template>
                </v-data-table>


            </v-col>
        </v-row>
    </v-container>
</template>

<script>
  // Table info.
  import tableData from './sampleDataTable';

  export default {
    data() {
      return {
        // We need some values for our select.
        caloriesList: [
          {text: "All", value: null},
          {text: "Only 237", value: 237},
          {text: "Only 305", value: 305},
        ],

        // Filter models.
        dessertFilterValue: '',
        caloriesFilterValue: null,

        // Table data.
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
            filter: (value) => {
              // If this filter has no value we just skip the entire filter.
              if (!this.dessertFilterValue) {
                return true;
              }

              // Check if the current loop value (The dessert name)
              // partially contains the searched word.
              return value.toLowerCase().includes(this.dessertFilterValue.toLowerCase());
            },
          },
          {
            text: 'Calories',
            value: 'calories',
            filter: (value) => {
              // If this filter has no value we just skip the entire filter.
              if (!this.caloriesFilterValue) {
                return true;
              }

              // Check if the current loop value (The calories value)
              // equals to the selected value at the <v-select>.
              return value === this.caloriesFilterValue;
            },
          },
          {text: 'Fat (g)', value: 'fat'},
          {text: 'Carbs (g)', value: 'carbs'},
          {text: 'Protein (g)', value: 'protein'},
          {text: 'Iron (%)', value: 'iron'},
        ]
      },
    }
  }
</script>
