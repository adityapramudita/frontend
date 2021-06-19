<template>
  <div>
    <h1>Daftar Pekerjaan Kita</h1>
    <ul>
    <li v-for="item in todos" :key="item.id">{{item.deskripsi}}<button @click="hapus(item.id)">X</button></li>
    </ul>
    <input v-model="myText"/>
    <button @click="tambah">Add</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data: function () {
    return {
      todos: [],
      myText: ''
    }
  },
  created() {
    const username = localStorage.getItem('user')
    const password = localStorage.getItem('pass')
    axios.get('http://localhost:3030/todo'),{headers : {username, password}}.then(result => {
      this.todos = result.data
    })
  },
  methods: {
    tambah: function () {
      const username = localStorage.getItem('user')
      const password = localStorage.getItem('pass')
      const item = { deskripsi : this.myText }
      axios.post('http://localhost:3030/todo', item, {headers: {username, password}})
      .then(() => {
        this.todos.push(item)
      })
    },
    hapus: function (id) {
      const username = localStorage.getItem('user')
      const password = localStorage.getItem('pass')
      axios.delete(`http://localhost:3030/todo/${id}`, {headers: {username, password}})
    }
  },
}
</script>