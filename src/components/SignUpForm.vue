<template>
  <form>
    <label>Email:</label>
    <input type="email" required v-model="email" placeholder="Enter your email here">

    <label>Password:</label>
    <input type="password" required v-model="password" placeholder="Enter your password here">

    <label>Role:</label>
    <select v-model="role">
      <option value="" disabled hidden selected>Choose Role</option>
      <option value="Developer">Web Developer</option>
      <option value="Designer">Web Designer</option>
    </select>
    
    <div class="terms">
      <input type="checkbox" @click="termsClicked" required>
      <label>Accept Terms and Conditions</label>
    </div>

    <button type="submit" @click.prevent="submitFormHandler">Submit Form</button>
  </form>

  <p>{{ email }}</p>
  <p>{{ password }}</p>
  <p>{{ role }}</p>
</template>

<script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        role: '',
        terms: false,

        termsClicked() {
          this.terms = !this.terms;
        },

        submitFormHandler() {

          if (this.terms === true) {
            console.log(
              'Email: ', this.email, '\n',
              'Password: ', this.password, '\n',
              'Role: ', this.role, '\n',
            )
          } else {
            console.log('Accept Terms and Conditions')
          }
        },
        }
      }
    }
</script>

<style>
  form {
    max-width: 420px;
    margin: 30px auto;
    background: white;  
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
</style>