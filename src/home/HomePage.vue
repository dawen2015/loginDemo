<template>
  <div style="width:57.14rem;border:0.08rem solid blue;border-radius:0.43rem;padding:3.57rem;">
    <h2>Personal Information</h2>
    <div
      style="width:100%;height:1rem;display: flex;
  align-items: center;
  justify-content: center;margin-bottom:2rem;margin-top:2rem"
    >
      <div style="width:7.14rem;height:0.22rem;background:#AF5BC1"></div>
    </div>
    
    
    <form @submit.prevent="handleSubmit">
      <div class="row">
        <div class="form-group input-container col-4">
          <i class="fa fa-user-shield icon"></i>
          <input
            type="text"
            v-model="currentUser.firstName"
            name="firstName"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && !ccurrentUser.firstName}"
            placeholder="First Name"
          />
          <div v-show="submitted && !email" class="invalid-feedback">First Name is required</div>
        </div>

        <div class="form-group input-container col-4">
          <i class="fa fa-user-shield icon"></i>
          <input
            type="text"
            v-model="currentUser.middleName"
            name="middleName"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && !email }"
            placeholder="Middle Name"
          />
          <div v-show="submitted && !email" class="invalid-feedback">Middle name is required</div>
        </div>

        <div class="form-group input-container password-box col-4">
          <i class="fa fa-user-shield icon"></i>
          <input
            type="text"
            v-model="currentUser.lastName"
            name="lastName"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && !password }"
            placeholder="Password"
          />
          <div v-show="submitted && !password" class="invalid-feedback">Last name is required</div>
        </div>
      </div>
      <div class="row">
        <div class="form-group input-container col-12">
          <i class="fa fa-address-card icon"></i>
          <input
            type="text"
            v-model="currentUser.address"
            name="address"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.address }"
            placeholder="Address 1"
          />
          <div v-show="submitted && ! currentUser.address" class="invalid-feedback">Address is required</div>
        </div>

      </div>
        <div class="row">
        <div class="form-group input-container col-12">
          <i class="fa fa-address-card icon"></i>
          <input
            type="text"
            v-model="currentUser.address2"
            name="address2"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.address2 }"
            placeholder="Address 2 (optional)"
          />
         
        </div>

      </div>
      <div class="row">
        <div class="form-group input-container col-6">
          <i class="fa fa-address-card icon"></i>
          <input
            type="text"
            v-model="currentUser.city"
            name="city"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.city }"
            placeholder="City"
          />
          <div v-show="submitted && ! currentUser.city" class="invalid-feedback">City is required</div>
        </div>
        <div class="form-group input-container col-6">
          <i class="fa fa-address-card icon"></i>
          <input
            type="text"
            v-model="currentUser.state"
            name="state"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.state }"
            placeholder="State"
          />
          <div v-show="submitted && ! currentUser.state" class="invalid-feedback">State is required</div>
        </div>
        
      </div>
 <div class="row">
        <div class="form-group input-container col-6">
          <i class="fa fa-address-card icon"></i>
          <input
            type="text"
            v-model="currentUser.zipcode"
            name="zipcode"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.zipcode }"
            placeholder="Zip/Postal Code"
          />
          <div v-show="submitted && ! currentUser.zipcode" class="invalid-feedback">Zip Code is required</div>
        </div>
        <div class="form-group input-container col-6">
          <i class="fa fa-flag-usa icon"></i>
          <input
            type="text"
            v-model="currentUser.country"
            name="country"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.country }"
            placeholder="Country"
          />
          <div v-show="submitted && ! currentUser.state" class="invalid-feedback">Country is required</div>
        </div>
        
      </div>
 <div class="row">
        <div class="form-group input-container col-6">
          <i class="fa fa-calendar-day icon"></i>
          <input
            type="text"
            v-model="currentUser.dob"
            name="dob"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.dob }"
            placeholder="Date of Birth"
          />
          <div v-show="submitted && ! currentUser.dob" class="invalid-feedback">Date of Birth is required</div>
        </div>
        <div class="form-group input-container col-6">
          <i class="fa fa-flag-usa icon"></i>
          <input
            type="text"
            v-model="currentUser.ssn"
            name="ssn"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.ssn }"
            placeholder="SSN or TIN"
          />
          <div v-show="submitted && ! currentUser.state" class="invalid-feedback">SSN is required</div>
        </div>
        
      </div>

   <div class="row">
        <div class="form-group input-container col-6">
          <i class="fa fa-money-check-alt icon"></i>
          <input
            type="text"
            v-model="currentUser.sourceoffund"
            name="sourceoffund"
            class="form-control input-field"
            :class="{ 'is-invalid': submitted && ! currentUser.sourceoffund }"
            placeholder="Source of Funds"
          />
          <div v-show="submitted && ! currentUser.sourceoffund" class="invalid-feedback">Source of funds is required</div>
        </div>
      
        
      </div>

       <div
      style="width:100%;height:1rem;display: flex;
            align-items: center;
            justify-content: center;margin-bottom:2rem;margin-top:2rem;"
        >
        
      <div style=""><input style="margin-top:0.1rem;" type="checkbox" id="acknowlege" name="acknowledge" ><span style="margin-left:0.5rem">Yes, I am an accredited investor</span></div>
    </div>

 <div
      style="width:100%;height:1rem;display: flex;
            align-items: center;
            justify-content: center;margin-bottom:2rem;padding-top:2rem"
        >
       <div class=" next-btn" :disabled="loading">NEXT <i class="fa fa-chevron-right next-icon" ></i></div>
    </div>

      <div v-if="error" class="alert alert-danger">{{error}}</div>
    </form>
    <p>
      <router-link to="/login">Logout</router-link>
    </p>
  </div>
</template>

<script>
import { userService } from "../_services";

export default {
  data() {
    return {
      user: {},
      users: [],
      currentUser:{}
    };
  },
  created() {
    this.user = JSON.parse(localStorage.getItem("user"));
    this.users.loading = true;
    userService.getAll().then(users => (this.currentUser = users[0]));
  }
};
</script>

<style scoped>
.next-btn{
    font-size: 1.28rem;
    background:lightgrey;
    padding:0.5rem;
    color: #000000;
    border-radius:2rem;
    padding:2rem;
}

.next-icon {
  margin-left: 0.5rem;
}
</style>