<template>
  <div>
    <h1>Daftar User Kita</h1>
    <ul>
    <li v-for="item in todos" :key="item.id">{{item.deskripsi}}<button @click="hapus(item.id)">X</button></li>
    </ul>
    <input v-model="username"/>
    <input v-model="password"/>
    <button @click="tambah">Add</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data: function () {
    return {
      users: [],
      username: '',
      password: ''
    }
  },
  created() {
    const username = localStorage.getItem('user')
    const password = localStorage.getItem('pass')
    axios.get('http://localhost:3030/user'),{headers : {username, password}}.then(result => {
      this.todos = result.data
    })
  },
  methods: {
    tambah: function () {
      const username = localStorage.getItem('user')
      const password = localStorage.getItem('pass')
      const item = { deskripsi : this.myText }
      axios.post('http://localhost:3030/user', item, {headers: {username, password}})
      .then(() => {
        this.todos.push(item)
      })
    },
    hapus: function (id) {
      const username = localStorage.getItem('user')
      const password = localStorage.getItem('pass')
      axios.delete(`http://localhost:3030/user/${id}`, {headers: {username, password}})
    }
  },
}
</script>