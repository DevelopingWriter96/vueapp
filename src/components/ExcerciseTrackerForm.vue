<template>
  <div id="excercise-form">
      <form @submit.prevent='handleSubmit'>
          <label>Date</label>
          <input v-model="item.date" type="date" />
          <label>Excercise Name</label>
          <input v-model="item.name" type="text" />
          <label>Amount</label>
          <input v-model="item.amount" type="text" />
          <button>Add Excercise</button>
      </form>
  </div>
</template>

<script>
export default {
    name: 'excercise-form',
    data () {
        return {
            item: {
                date: '',
                name: '',
                amount: '',          
            }, 
        }
    },
    methods: {
        handleSubmit(){
            this.$emit('add:item', this.item)
            this.item = {
                date: '',
                name: '',
                amount: '',   
            }
        }
    }

}
</script>

<style>

</style>