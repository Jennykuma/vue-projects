<template>
  <div class="container">
    <Navbar />
    <ChatWindow />
    <NewChatForm />
  </div>
</template>

<script>
import { useRouter } from 'vue-router'
import { watch } from 'vue'
import ChatWindow from '../components/ChatWindow'
import Navbar from '../components/Navbar'
import NewChatForm from '../components/NewChatForm'
import getUser from '../composables/getUser'

export default {
  components: { Navbar, NewChatForm, ChatWindow },
  setup() {
    const { user } = getUser()
    const router = useRouter()

    // watch user
    // fires the function when user changes
    watch(user, () => {
      if (!user.value) {
        router.push({ name: 'Welcome' })
      }
    })
  }
}
</script>

<style>
</style>