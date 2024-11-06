<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <h1>Welcome to My Page!</h1>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="6">
        <v-card>
          <v-card-title>
            <h2>About Me</h2>
          </v-card-title>
          <v-card-text>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla nec elit eget arcu tincidunt fermentum. Sed auctor, nunc id lacinia tincidunt, nisl nisl tincidunt urna, id ultrices nunc risus id nunc.</p>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="6">
        <v-card>
          <v-card-title>
            <h2>My Projects</h2>
          </v-card-title>
          <v-card-text>
            <ul>
              <li>Project 1</li>
              <li>Project 2</li>
              <li>Project 3</li>
            </ul>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
  import axios from 'axios'
  axios.get(`http://localhost/user/${localStorage.getItem('id')}/interest`)
    .then((res) => {
      console.log(res.data)
    })
</script>
