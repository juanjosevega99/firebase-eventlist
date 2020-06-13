<script>
  import { firebaseConfig, githubAuthProvider } from '../utils/firebase'
  import { onMount } from 'svelte'

  onMount(async () => {
    firebaseConfig
      .auth()
      .onAuthStateChanged(user => {

      })
  })

  const handleLoginWithGithub = () => {
    firebaseConfig
      .auth()
      .signInWithPopup(githubAuthProvider)
      .then(response => console.log(response))
      .catch(error => console.log(error))
  };

  const handleLogout = () => {
    firebaseConfig
      .auth()
      .signOut()
      .then(() => {
        console.log('Session closed')
      })
      .catch(error => console.log(error))
  };

</script>

<style>

</style>

<div class="App">
  <h1>EventList</h1>
  <button on:click={handleLoginWithGithub}>Login with GitHub</button>
  <button on:click={handleLogout}>Logout</button>

  {#if isLogin}
</div>