<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>Vue.js 2 & Firebase Sample application</h1>
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">
        <h3>Books Lists</h3>
      </div>
      <div class="panel-body">
        <table class="table table-striped">
          <thead>
            <tr>
              <th>Title</th>
              <th>Author</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="book in books" :key="book">
              <td>t<a v-bind:href="book.url">{{book.title}}</a></td>
              <td>a{{book.author}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    books:{{books}}
    <!-- <router-view/> -->
  </div>
</template>

<script>
import Firebase from 'firebase';

let config = {
  apiKey: "AIzaSyAYM9hPdIceVgz_SSyL1kbUAnva9_jo3h0",
  authDomain: "vuejs-workouts.firebaseapp.com",
  databaseURL: "https://vuejs-workouts-default-rtdb.firebaseio.com",
  projectId: "vuejs-workouts",
  storageBucket: "vuejs-workouts.appspot.com",
  messagingSenderId: "164938302981",
  appId: "1:164938302981:web:48a3e2660c80418b037e6c",
  measurementId: "G-LELS1LGKDJ"
}

let app = Firebase.initializeApp(config);
let db = app.database();
let booksRef = db.ref('books');

export default {
  name: 'App',
  firebase: function () {
    return {
      books: booksRef
    }
  },
  data(){
    return {
      books: booksRef
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
