<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <Button/>
    <ToOtherPageBtn/>
    <br/>
    <LoginForm/>
  </div>  
</template>

<script>
import Button from '@/components/Button.vue'
import ToOtherPageBtn from '@/components/ToOtherPageBtn.vue'
import LoginForm from '@/components/LoginForm.vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    Button,
    ToOtherPageBtn,
    LoginForm,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
