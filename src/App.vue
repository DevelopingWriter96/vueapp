<template>
  <ExcerciseTrackerForm @add:item='addItem' />
  <ExcerciseTracker 
  @delete:item='deleteItem'
  @edit:item='editItem' 
  :items='excerciseItems'/>
</template>

<script>
import ExcerciseTracker from './components/ExcerciseTracker.vue'
import ExcerciseTrackerForm from './components/ExcerciseTrackerForm.vue'

export default {
  name: 'App',
  components: {
    ExcerciseTracker,
    ExcerciseTrackerForm
  },
data() {
  return {
    excerciseItems: [
        {
          id: 1,
          date: '2021-05-04',
          name: 'Force Push-ups',
          amount: '100 reps',
        },

        {
          id: 2,
          date: '2021-05-04',
          name: 'Force Pull-ups',
          amount: '100 reps',
        },

        {
          id: 3,
          date: '2021-05-04',
          name: 'Scarlacc Squats',
          amount: '100 reps',
        },

        {
          id: 4,
          date: '2021-05-04',
          name: 'Rebel Run',
          amount: '6.21371 miles',
        },
      ]
    }
  },
  methods: {
    addItem(item) {
     const lastId = this.excerciseItems.length > 0
     ? this.excerciseItems[this.excerciseItems.length -1].id
     : 0;

     const id = lastId + 1; 
      
     const newItem = { ...item, id}

     this.excerciseItems = [ ...this.excerciseItems, newItem]
    },
    deleteItem(id) {
      this.excerciseItems = this.excerciseItems.filter(item => item.id !== id)
    },
    editItem(id, updatedItem) {
      this.excerciseItems = this.excerciseItems
        .map(item => {
          return item.id === id ? updatedItem : item
        })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
