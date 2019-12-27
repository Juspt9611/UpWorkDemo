<template>
  <v-container>
    <v-layout text-center wrap>
      <v-flex mb-4>
        <h1 class="headline font-weight-bold my-3">Juan Manuel Coyotzi Arellano - Proposal</h1>
        <p class="subheading font-weight-regular">
          email: ju_9611spt@outlook.com
        </p>
      </v-flex>

      <v-flex xs12>
        <v-expansion-panels>
          <v-expansion-panel>
            <v-expansion-panel-header>1) In the example below, how would you create a two way data binding between the 'someDataField' variable and the HTML element with an ID of 'address' ?</v-expansion-panel-header>
            <v-expansion-panel-content>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="6">
                    <p>The first option could be with the v-model property</p>
                  </v-col>
                  <v-col cols="12" sm="6">
                    <v-text-field label="Regular" v-model="someDataField"></v-text-field>
                    <p>The address is: {{ someDataField }}</p>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col cols="12" sm="6">
                    <p>The second option could be with and OnChange method on the input field</p>
                  </v-col>
                  <v-col cols="12" sm="6">
                    <v-text-field label="Regular" @change="setNewData"></v-text-field>
                    <p>The address is: {{ someDataField2 }}</p>
                  </v-col>
                </v-row>
              </v-container>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-expansion-panel>
            <v-expansion-panel-header>2) How would you display the total age of everyone in myArray in the commented section below?</v-expansion-panel-header>
            <v-expansion-panel-content>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="6">
                    <p>I would use a method to read the array and make the operation.</p>
                  </v-col>
                  <v-col cols="12" sm="6">
                    <p>Total age: {{ getTotalAge() }}</p>
                  </v-col>
                </v-row>
              </v-container>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-expansion-panel>
            <v-expansion-panel-header>3) How would you print all the objects in this array that have an age less than 33 ?</v-expansion-panel-header>
            <v-expansion-panel-content>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="6">
                    <p>I would use a method to read the array and make the filter by age.</p>
                  </v-col>
                  <v-col cols="12" sm="6">
                    <p>{{ filterByAge() }}</p>
                  </v-col>
                </v-row>
              </v-container>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-expansion-panel>
            <v-expansion-panel-header>4) How would you select the total salary of everyone in this table who has an age below 33 ?</v-expansion-panel-header>
            <v-expansion-panel-content>
              <v-container>
                <v-row>
                  <v-col cols="12">
                    <span>{{MYSQLquery}}</span>
                  </v-col>
                </v-row>
              </v-container>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-expansion-panel>
            <v-expansion-panel-header>5) display the data in myArray here using Vuetify components</v-expansion-panel-header>
            <v-expansion-panel-content>
              <v-simple-table>
                <template v-slot:default>
                  <thead>
                    <tr>
                      <th class="text-left">Name</th>
                      <th class="text-left">Age</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="data in myArray" :key="data.name">
                      <td>{{ data.name }}</td>
                      <td>{{ data.age }}</td>
                    </tr>
                  </tbody>
                </template>
              </v-simple-table>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    someDataField: "",
    someDataField2: "",
    myArray: [
      { name: "Kai", age: 35 },
      { name: "Pat", age: 31 },
      { name: "Eman", age: 30 }
    ],
    MYSQLquery: "SELECT SUM(Salary) FROM TABLENAME WHERE Age < 33"
  }),
  methods: {
    setNewData(value) {
      this.someDataField2 = value;
    },
    getTotalAge() {
      // I prefer to use the foreach function but there is also a functional aproach with the reduce function
      let totalAge = 0;
      this.myArray.forEach(data => {
        totalAge += data.age;
      });
      return totalAge;
    },
    filterByAge() {
      // I prefer to use the foreach function but there is also a functional aproach with the filter function
      let tempArray = [];
      this.myArray.forEach(data => {
        if (data.age < 33) {
          tempArray.push(data);
        }
      });
      return tempArray;
    }
  }
};
</script>
