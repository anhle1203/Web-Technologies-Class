<!-- Life cycle of Vue JS applications
 1. Set up the data observation (entry/setup())
 2. Compile template
 3. Mount itself to DOM
 4. Update the DOm

 Vue Lifecycle States:
 Setup ==> Before mount ==> Mounted ==> Before update ==> Updated ==> Mounted (cycle)
                      (after cycle) ==> Before unmount ==> Unmounted`
 -->
 <template>
    <h1>{{ message }}</h1>
    <div class="card">
      <h2 ref="title">This is the App component.</h2>
      <h2>Number: {{ number }}</h2>
      <button @click="number++">Increment number by one</button>
      <button @click="isShow = !isShow">Toggle component1</button>
      <Component1 v-if="isShow"></Component1>
    </div>
  </template>
  
  <script setup>
  import {
    ref,
    onBeforeMount,
    onMounted,
    onBeforeUpdate,
    onUpdated,
    onBeforeUnmount,
    onUnmounted,
    watch
  } from 'vue'
  
  import Component1 from './Component1.vue'
  
  let message = ref('Hello, Lifecycle Hooks!')
  
  let number = ref(1)
  let title = ref(null)
  
  let isShow = ref(true)
  
  console.log('App component is setup.')
  
  onBeforeMount(() => {
    console.log('App component is before mount.')
    console.log(number.value) // The ref data works.
    console.log(title.value) // Since the component has not yet been mounted, you won't have access to the component's template or DOM elements within onBeforeMount.
  })
  onMounted(() => {
    console.log('App component is mounted.')
    console.log(title.value) // This works once the component is mounted.
  })
  /* A component is considered mounted after:
    1. All of its synchronous child compoenents have been mounted
    2. Its own DOM tree has been created and inserted into the parent container
  */
  onBeforeUpdate(() => {
    console.log('App component is before update.')
  })
  onUpdated(() => {
    console.log('App component is updated.')
  })
  onBeforeUnmount(() => {
    console.log('App component is before unmount.')
  })
  onUnmounted(() => {
    console.log('App component is unmounted.')
  })
  watch(number, () => {
    console.log('number changes!')
  })
  </script>
  
  <style scoped>
  .card {
    background-color: purple;
    color: white;
    padding: 20px 10px;
    margin-bottom: 10px;
  }
  </style>