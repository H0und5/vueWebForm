<template>
  <form>

    <!-- Account Information -->

    <label>Email:</label>
    <input type="email" required v-model="email" placeholder="Enter your email here">

    <label>Password:</label>
    <input type="password" required v-model="password" placeholder="Enter your password here">

    <!-- Select Role -->
    
    <label>Role:</label>
    <select v-model="role">
      <option value="" disabled hidden selected>Choose Role</option>
      <option value="Developer">Web Developer</option>
      <option value="Designer">Web Designer</option>
    </select>

    <!-- Skills -->

    <label>Skills:</label>
    <input type="text" required v-model="tempSkills" @keydown="addSkill"/>

    <!-- Accept Terms and Conditions -->

    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label>Accept Terms and Conditions</label>
    </div>

    <!-- Form Submit Button -->

    <button type="submit" @click.prevent="submitFormHandler">Submit Form</button>
  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
  <p v-for="skill in skills">Skills: {{ skill }}</p>
</template>

<script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        role: '',
        terms: false,
        tempSkills: '',
        skills: [],
        }
      },

    methods: {
      addSkill(e) {

        if (e.key === ',' && this.tempSkills !== '') {
          console.log(e.target.value);
          
          this.skills.push(this.tempSkills);

          this.tempSkills = '';

        }

        // this.skills.push(this.tempSkills);

        // this.tempSkills = '';
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