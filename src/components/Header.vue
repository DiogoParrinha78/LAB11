<template>
    <div id="nav">
       <router-link to="/" id="logo_url">
        <img src="../assets/images/mips_logo.png" id="logo">
       </router-link>
    <router-link to="/basket">
        <img src="../assets/images/shop.png" id="logo2">
    </router-link>
    <router-link to="/login">Login</router-link>
    <router-link to="/register">Register</router-link>
    
    </div>
    </template>
    
    <script>
    
    export default {
        methods: {	
    
        },
        computed: {
            
        },
    }
    
    
    </script> 
    
    <style scoped>
    #nav{
        background-color: #222;
        padding: 15px 50px;
        color: #00FF00;
        display:flex;
        justify-content: flex-end;
        align-items: center;
       
    }
    
    #nav #logo_url{
        margin: auto;
        margin-left: 0;
    }
    
    #logo{
        width: 100px;
        height: 80px;
    }
    
    #logo2{
        width: 100px;
        height: 80px;
    }
    
    #nav a{
        color: #00FF00;
        text-decoration:  none;
        margin: 12px;
        transition: .5s;
    }
    
    #nav a:hover{
        color: #fff;
    }
    
    
    </style>
    
    