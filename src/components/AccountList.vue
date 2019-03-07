<template>
    <div id="account-list">
        <h1>{{title}}</h1>
    <ul>
        <li v-for="account in accounts" v-bind:key="account">
            <div>
                <p><b>{{ account.accountname }}</b></p>
                <p>Tipo: {{account.accounttypestring}}</p>
                <p>Saldo: {{ account.balanceformatted }} {{account.currencyid}}</p>
                <p>Aberta em: {{ account.openingdate }}</p>
                <!--a v-bind:href="account.accountname" target="_blank" rel="noopener">{{ account.accountname }} ({{account.accounttypestring}})</a-->
            </div>
            
        </li>
    </ul>
    </div>
</template>

<script>
const axios = require('axios');

export default {
    props: {
        msg: String
    },
    methods:{
        initList(accounts) {
            this.accounts = accounts
        }
    },
    data() {
        return {
            title: "Account list",
            accounts: []
        }
    },        
    mounted() {
        axios
            .get('http://localhost:8000/api/accounts/?limit=100')
            .then(response => {                
                this.initList(response.data.results);
            })
    }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
  padding: 5px;  
}
a {
  color: #42b983;
}
</style>