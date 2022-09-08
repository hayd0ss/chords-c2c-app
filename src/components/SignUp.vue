<template>
  <section class="signup">
    <div class="body">
      <form id="signup-form" @submit.prevent="checkForm" ref="registerForm" action="#" novalidate="true">
        <div class="signup-div">
          <div class="signup-header">
            <h2>Sign Up to Chord</h2>
          </div>
          <div class="user-input">
            <div class="input user-name">
              <p>Username</p>
              <input type="text" v-model="userDetails.userName" class="input" placeholder="Enter username">
            </div>
            <div class="input user-email">
              <p>Email address</p>
              <input type="text" v-model="userDetails.userEmail" class="input" placeholder="Enter email">
            </div>
            <div class="input user-password">
              <p>Password</p>
              <div class="password">
                <!-- CHANGE TO 8 minlength="8" LATER!!! -->
                <input type="password" v-model="userDetails.userPassword" class="input"
                  placeholder="Enter password (min 8 characters)">
              </div>
            </div>
          </div>

          <div class="errors">
            <p v-if="errors.length">
              <b class="error-note">Please correct the following error(s):</b>
            <ul>
              <li v-for="error in errors">{{ error }}</li>
            </ul>
            </p>
          </div>

          <input type="submit" class="sign-up-btn" value="Sign up" />
          <!-- <input type="button" @click="checkForm" class="sign-up-btn" value="Sign up" /> -->

        </div>
      </form>
    </div>
  </section>
</template>

<script>
// const axios = require("axios");
// import axios from 'axios';
// const formData = require("form-data");
const userApi = "https://vc-users-login.netlify.app/.netlify/functions/api/"
export default {
  name: "SignUp",
  data () {
    return {
      userDetails: {
        userName: '',
        userEmail: '',
        userPassword: '',
      },
      errors: [],
      dialog: true,

    }
  },
  methods: {
    checkForm (e) {
      this.errors = [];

      if (this.validEmail(this.userDetails.userEmail) && this.userDetails.userPassword.length >= 8 && this.userDetails.userName && this.userDetails.userPassword && this.userDetails.userEmail) {
        return this.addUser()
      }

      if (!this.userDetails.userName) {
        this.errors.push("Name required.");
      }
      if (!this.userDetails.userEmail) {
        this.errors.push('Email required.');
      } else if (!this.validEmail(this.userDetails.userEmail)) {
        this.errors.push('Valid email required.');
      }
      if (!this.userDetails.userPassword) {
        this.errors.push("Password required.");
      } else if (this.userDetails.userPassword.length <= 8) {
        this.errors.push("Password needs to be longer than 8 characters.");
      }

      if (!this.errors.length) {
        return true;
      }

      e.preventDefault();
    },
    validEmail (userEmail) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(userEmail);
    },
    addUser () { // done
      fetch(userApi, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(this.userDetails)
      })
        .then((response) => response.text())
        .then((data) => {
          this.resetData()
          console.log(data)
        })
        .catch((err) => {
          if (err) throw err;
        })
    },
    resetData () {
      // this.editId = ''
      this.userDetails.userName = ''
      this.userDetails.userEmail = ''
      this.userDetails.userPassword = ''
    },
  }
}

</script>

<style lang="scss" scoped>
.signup-div {
  background-color: white;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 20rem;
  width: 30rem;
  padding: 4rem 6rem 6rem 6rem;

  p {
    font-size: 0.8rem;
  }

  a {
    font-size: 0.8rem;
    font-weight: 600;
    cursor: pointer;
  }
}

.signup-header {
  display: flex;
  align-items: baseline;
  margin-bottom: 1rem;
}


.user-input {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 60%;
  justify-content: space-between;
  margin: 2rem 0rem;
}

.input {
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 1rem;


  input {
    font-size: 1rem;
    height: 2.5rem;
    width: 100%;
    margin-top: 0.5rem;
    margin-bottom: 5px;
    padding: 10px;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    border: 1px solid black;
  }

  span {
    font-weight: 600;
    cursor: pointer;
  }

  span:hover {
    text-decoration: underline;
  }

}

.sign-up-btn {
  margin-top: 2rem;
  margin-bottom: 1.5rem;
  font-weight: 700;
  width: 100%;
  min-height: 2.5rem;
  border: 1px solid black;
  background-color: black;
  color: white;
  cursor: pointer;
}

.errors {
  text-align: left;
}

.errors p {

  padding-top: 1em;
  font-weight: 500;
  color: tomato;
}

.error-note {
  color: black;
  font-size: 1rem;
}
</style>