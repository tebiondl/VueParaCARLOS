<template>
  <div class="LoginForm">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group id="exampleInputGroup1" label="Email address:" label-for="exampleInput1">
        <b-form-input
          id="exampleInput1"
          type="email"
          v-model="form.email"
          required
          placeholder="Enter email"
          autocomplete="off"
        />
      </b-form-group>

      <b-form @submit.prevent class="passwordField">
        <label for="textPassword">Password</label>
        <b-input type="password" id="textPassword" aria-describedby="passwordHelpBlock" v-model="form.password" required
          placeholder="Enter password"/>
      </b-form>

      <b-form @submit.prevent class="passwordField2">
        <label for="textPassword">Repeat Password</label>
        <b-input type="password" id="textPassword" aria-describedby="passwordHelpBlock" v-model="password2" required
          placeholder="Enter password"/>
      </b-form>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      form: {
        email: "",
        password: "",
      },
      password2: "",
      show: true
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      if(this.form.password != this.password2){

        alert("Passwords do not match");
        this.form.email = "";
        this.form.password = "";
        this.password2 = "";
      }else{
        const finalJSON = JSON.stringify(this.form);
        alert(finalJSON);

        const http = new XMLHttpRequest();
        const url = 'http://localhost:3000/user'
        
        axios({
          method: 'post',
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json',
          },
          url: url,
          data: finalJSON
        });
      }       
    },
    onReset(evt) {
      evt.preventDefault();
      /* Reset our form values */
      this.form.email = "";
      this.form.password = "";
      /* Trick to reset/clear native browser form validation state */
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    }
  }
};
</script>

<style scoped>
.LoginForm {
  position: relative;
  margin-top: 5%;
  margin-bottom: 5%;
  margin-right: 20%;
  margin-left: 20%;
}

.passwordField {
    margin-bottom: 1.4%;
}

.passwordField2 {
    margin-bottom: 5%;
}
</style>
