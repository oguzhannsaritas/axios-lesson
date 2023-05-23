

<template>
  <div class="container py-5">
    <h1 class="text-center">
      Axios Kullanımı
    </h1>
    <div class="row">
      <div class="col-md-7 offset-md-3">
        <div class="card">
          <div class="card-header">
            listeler
          </div>
          <div class="card-body" style="overflow: auto; height: 300px;">
            <ul v-if="todoİsLoadin==false" class="list-group">
              <li v-for="(todo, index) in todos" :key="index" class="list-group-item">
                {{ todo.title }}
              </li>
            </ul>
            <h5 v-else>Yükleniyor..</h5>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "App",
  data() {
    return {
      url: "https://jsonplaceholder.typicode.com/todos",
      todos: [],
      todoİsLoadin: true
    }
  },
  created() {
    setTimeout(()=>{
      axios.get(this.url)
      .then(response => (this.todos = response.data))
      .finally(()=>(this.todoİsLoadin = false));
    },3000)
  },

}
</script>

<style scoped></style>
