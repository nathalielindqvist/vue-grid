<template>
  <v-container class="grey lighten-5">
    <v-row no-gutters>
      <v-col
        v-for="n in ['Hello', 'big', 'world']"
        :key="n"
        cols="12"
        sm="4"
      >
      <v-card
    class="mx-auto"
    max-width="400"
    tile
  >
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title>{{n}}</v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title>Two-line item</v-list-item-title>
        <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>

    <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title>Three-line item</v-list-item-title>
        <v-list-item-subtitle>
          Secondary line text Lorem ipsum dolor sit amet,
        </v-list-item-subtitle>
        <v-list-item-subtitle>
          consectetur adipiscing elit.
        </v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
  </v-card>
      </v-col>
    </v-row>
    <br />
    <hr>
    <br />
     <v-card>
    {{result}}
  </v-card>
  </v-container>
 
</template>

<script>


export default {
  data: () => {
    return {
      result: '',
      responseAvailable: false,
      }
  },
  mounted() {
    this.fetchData();
    },
    methods: {
      fetchData() {
        this.responseAvailable = false;

        fetch("https://reqres.in/api/users/2", {
          "method": "GET",
        })
        .then(response => {
          if(response.ok){
            response.json().then(response => {
              this.result = response;
              this.responseAvailable = true;
              })
          } else {
            alert("Server returned " + response.status + " : " + response.staturText);
          }
        })
        .catch(err => {
          console.log(err);
       });
      }
    }
};
</script>
