<template>
  <div class="container">
    <NavBar/> 
    <ChatWindow/>
    <NewChatForm/> 
  </div>
</template>

<script>
//get thye current user using the getUser composable
//Watch tyhe current user for change
//redirect the user to the welcome  page when they are logged out  

import NavBar from '@/components/NavBar'
import getUser from '@/composables/getUser'
import { watch } from 'vue'
import { useRouter } from 'vue-router'
import NewChatForm from '@/components/NewChatForm'
import ChatWindow from '@/components/ChatWindow'

export default {
    components: {NavBar, NewChatForm, ChatWindow},
    setup(){

        const {user} = getUser()
        const router = useRouter()

        watch(user, () => {
            if(!user.value){
                router.push({name: 'Welcome'})
            }
        })
    }

}
</script>

<style>

</style>