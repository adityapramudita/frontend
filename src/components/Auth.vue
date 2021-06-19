<template>
    <div>
        <div>
            <label>username</label>
            <input type="text" v-model="username"/>
        </div>
        <div>
            <label>password</label>
            <input type="password" v-model="password"/>
        </div>
        <button @click="simpan">simpan</button>
        <button @click="hapus">hapus</button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            username: '',
            password: ''
        }
    },
    created() {
        this.username = localStorage.getItem('user')
        this.password = localStorage.getItem('pass')
    },
    method: {
        simpan: function() {
            localStorage.setItem('user', this.username)
            localStorage.setItem('pass', this.password)
        },
        hapus: function() {
            localStorage.removeItem('user')
            localStorage.removeItem('pass')
            this.username = ''
            this.password = ''
        }
    }
}
</script>