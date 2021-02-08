<template>
  <div id="app">
    <main>
      <div class="wrapper">
        <header>
          <h1>Vue Todo List</h1>
        </header>
        <div class="search-box">
          <input type="text" class="search-bar" placeholder="Add a todo..." v-model="item" @keypress="addToListOnEnter" />
          <button class="add-button" v-on:click="addToList()">+</button>
        </div>
        <div class="list-todo">
          <ul style="list-style-type: none;">
            <li v-for="(todo, i) in todoList" v-bind:key='todo.id' class="indi-item">
              <button class="delete-button" @click="deleteItem(i)">X</button>
              <span>{{i + 1}}: {{todo.text}}</span>
            </li>
          </ul>
        </div>
      </div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return{
      item: '',
      todoList: [
        {text: 'Learn Vue.js', id: 0},
        {text: 'Build vue todo list', id:1},
        {text: 'Learn more Vue.js', id: 2},
      ]
    }
  },
  methods: {
    addToList(){
      this.todoList.push({
            text: this.item,
            id: new Date().valueOf()
          }),
          this.item = ''
    },
    addToListOnEnter(e){
      if(e.key && e.key == 'Enter'){
        this.todoList.push({
            text: this.item,
            id: new Date().valueOf()
        }),
        this.item = ''
      }
    },
    deleteItem(i){
      this.todoList.splice(i, 1);
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Indie+Flower&display=swap');
* {
padding: 0;
margin: 0;
box-sizing: border-box;
}

body {
  font-family: 'Indie Flower', cursive;
  background-color: #f6f6f6;
}

.wrapper header h1 {
  text-align: center;
  margin-top: 2rem;
  margin-bottom: 3rem;
  color: #161d6f;
  text-decoration: underline;
}

.search-box {
  text-align: center;
}

.search-box input{
  border: none;
  border-left: solid 3px #161d6f;
  border-bottom: solid 3px #161d6f;
  padding-left: .5rem;
  padding-bottom: .2rem;
  font-size: 1.2rem;
  background: transparent;
  transition: .5s;
}

.search-box input:focus {
  outline: none;
  box-shadow: -3px 3px gray;
  transition: .5s;
}

.search-box button {
  font-size: 1.2rem;
  padding: .25rem .6rem;
  margin-left: 1rem;
  border: solid 3px #161d6f;
  background: transparent;
  border-radius: 10rem;
}

.list-todo { 
  margin-left: 10%;
  margin-top: 4rem;
}

.list-todo li{
  margin-top: 1rem;
}

.list-todo li span {
  text-decoration: underline;
  margin-left: 1.5rem;
  font-size: 1.4rem;
}

.list-todo li button{
  border: dashed 2px black;
  border-radius: 10rem;
  background-color: transparent;
  padding: .15rem .3rem;
}
</style>
