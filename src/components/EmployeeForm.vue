<template>
  <div id="employee-form">
    <form @submit.prevent="handleSubmit">
      <label>Employee name</label>
      <input v-model="employee.name" type="text" />
      <label>Employee Email</label>
      <input v-model="employee.email" type="text" />
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'employee-form',
    data() {
      return {
        employee: {
          name: '',
          email: '',
        },
      }
    },
    methods:{
        handleSubmit(){
            if(this.isInvalidName|| this.isInvalidEmail){
                alert('please fill the form')
            }
            else{
                this.$emit('add-employee', this.employee)
            }
        }
    },
    computed:{
        isInvalidName(){
            return this.employee.name.replace(/ /g, '')===''
        },
        isInvalidEmail(){
            return this.employee.email.replace(/ /g, '')===''
        }
    }
  }
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }
</style>