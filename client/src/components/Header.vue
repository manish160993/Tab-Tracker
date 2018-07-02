<template>
    <v-toolbar fixed class="cyan">
        <v-toolbar-title class="mr-4">
            <span class="home" @click="navigateTo({name:'/'})">
                 Tracker
            </span>
        </v-toolbar-title>
        <v-spacer/>
        <v-toolbar-items>
            <v-btn 
            flat dark @click="navigateTo({name:'login'})">
                    Login
            </v-btn>
        </v-toolbar-items>
        <v-toolbar-items>
            <v-btn 
            flat dark @click="navigateTo({name:'register'})">
                    SignUp
            </v-btn>
        </v-toolbar-items>
    </v-toolbar>
</template>

<script>
export default {
    methods:{
        navigateTo(route){
            this.$router.push(route)
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home{
    cursor: pointer;
}
.home:hover{
    color:aqua
}

</style>
