<template>
  <div class="login-container">
    <div class="top-container">
      <div class="login-text-info">
        <div class="login-text">Your email address has been verified!</div>
        <div class="login-text">Please sign in to continue creating your account.</div>
      </div>
      <div class="login-close-btn">
        <i class="fa fa-times" aria-hidden="true"></i>
      </div>
    </div>
    <div class="sign-in-container">
      <h3 class="sign-in-label">SIGN IN</h3>
      <form @submit.prevent="handleSubmit">
        <div class="form-group login-input input-container">
          <i class="fa fa-envelope-square icon"></i>
          <input
            type="text"
            v-model="email"
            name="email"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && !email }"
            placeholder="Email"
          />
          <div v-show="submitted && !email" class="invalid-feedback">Email is required</div>
        </div>
        
        <div class="form-group login-input input-container password-box">
          <i class="fa fa-key icon"></i>
          <input
            type="password"
            v-model="password"
            name="password"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && !password }"
            placeholder="Password"
          />
          <div v-show="submitted && !password" class="invalid-feedback">Password is required</div>
        </div>
        <div class="form-group sign-in-btn">
          <button class="btn btn-primary login-in-btn" :disabled="loading">SIGN IN</button>
          <img
            v-show="loading"
            src="data:image/gif;base64,R0lGODlhEAAQAPIAAP///wAAAMLCwkJCQgAAAGJiYoKCgpKSkiH/C05FVFNDQVBFMi4wAwEAAAAh/hpDcmVhdGVkIHdpdGggYWpheGxvYWQuaW5mbwAh+QQJCgAAACwAAAAAEAAQAAADMwi63P4wyklrE2MIOggZnAdOmGYJRbExwroUmcG2LmDEwnHQLVsYOd2mBzkYDAdKa+dIAAAh+QQJCgAAACwAAAAAEAAQAAADNAi63P5OjCEgG4QMu7DmikRxQlFUYDEZIGBMRVsaqHwctXXf7WEYB4Ag1xjihkMZsiUkKhIAIfkECQoAAAAsAAAAABAAEAAAAzYIujIjK8pByJDMlFYvBoVjHA70GU7xSUJhmKtwHPAKzLO9HMaoKwJZ7Rf8AYPDDzKpZBqfvwQAIfkECQoAAAAsAAAAABAAEAAAAzMIumIlK8oyhpHsnFZfhYumCYUhDAQxRIdhHBGqRoKw0R8DYlJd8z0fMDgsGo/IpHI5TAAAIfkECQoAAAAsAAAAABAAEAAAAzIIunInK0rnZBTwGPNMgQwmdsNgXGJUlIWEuR5oWUIpz8pAEAMe6TwfwyYsGo/IpFKSAAAh+QQJCgAAACwAAAAAEAAQAAADMwi6IMKQORfjdOe82p4wGccc4CEuQradylesojEMBgsUc2G7sDX3lQGBMLAJibufbSlKAAAh+QQJCgAAACwAAAAAEAAQAAADMgi63P7wCRHZnFVdmgHu2nFwlWCI3WGc3TSWhUFGxTAUkGCbtgENBMJAEJsxgMLWzpEAACH5BAkKAAAALAAAAAAQABAAAAMyCLrc/jDKSatlQtScKdceCAjDII7HcQ4EMTCpyrCuUBjCYRgHVtqlAiB1YhiCnlsRkAAAOwAAAAAAAAAAAA=="
          />
        </div>
        <div v-if="error" class="alert alert-danger">{{error}}</div>
      </form>
      <div class="login-help-text forget-label">Forgot Password?</div>
      <div class="login-help-text">Create Account</div>
    </div>
  </div>
</template>

<script>
import { router } from "../_helpers";
import { userService } from "../_services";

export default {
  data() {
    return {
      email: "",
      password: "",
      submitted: false,
      loading: false,
      returnUrl: "",
      error: ""
    };
  },
  created() {
    // reset login status
    userService.logout();
    // get return url from route parameters or default to '/'
    this.returnUrl = this.$route.query.returnUrl || "/";
  },
  methods: {
    handleSubmit(e) {
      this.submitted = true;
      const { email, password } = this;

      // stop here if form is invalid
      if (!(email && password)) {
        return;
      }

      this.loading = true;
      userService.login(email, password).then(
        user => router.push(this.returnUrl),
        error => {
          this.error = error;
          this.loading = false;
        }
      );
    }
  }
};
</script>

<style scoped>

.password-box {
  margin-top: 3.07rem;
}

.login-container {
  width: 35.71rem;
  position: fixed;
  right: 0rem;
  top: 0rem;
}

.login-container > .top-container {
  vertical-align: middle;
  color: #ffff;
  display: flex;
  padding-top: 1.29rem;
  padding-left: 2rem;
  padding-right: 1rem;
  padding-bottom: 1.22rem;
  background: #90cc1b;
}

.login-container > .top-container > .login-text-info {
  width: 100%;
}

.login-text {
  text-align: center;
}

.sign-in-container {
  box-shadow: 0px -4px 4px rgba(0, 0, 0, 0.5);
  background: #4d008c;
  padding-top: 2.86rem;
  padding-bottom: 2.86rem;
  padding-left: 3.57rem;
  padding-right: 3.57rem;
}
.sign-in-label {
  margin-bottom: 3.21rem;
  width: 100%;
  text-align: center;
}

.login-close-btn {
  margin-right: 1.43rem;
  margin-top: 0.4rem;
  font-size: 1.14rem;
  cursor: pointer;
}

.login-input {
  margin-bottom: 3.07rem;
}

.sign-in-btn {
  margin-top: 3.07rem;
  width: 100%;
  text-align: center;
}

.login-in-btn {
  padding-top: 1.07rem;
  padding-bottom: 1.07rem;
  font-size: 1.43rem;
  line-height: 1.43rem;
  background: #73eedc;
  color: #000000;
  border-radius: 1.43rem;
  width: 9.21rem;
}

.login-help-text {
  font-size: 1.14rem;
  color: #73eedc;
  text-align: center;
  cursor: pointer;
}

.forget-label {
  margin-top: 2.86rem;
  margin-bottom: 0.94rem;
}

.btn:hover {
  opacity: 1;
}


</style>