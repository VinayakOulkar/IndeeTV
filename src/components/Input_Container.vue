<template>
    <div id="InputContainer" class="">
        <div id="signIn" class="my-3"><span class="whitecolor">Sign in </span></div>
        <form @submit.prevent="submitForm">
            <!-- Email input field -->
            <div class="mb-3">
                <label class="form-label bluecolor" style="font-size:0.8rem;">Email</label>
                <input type="email" class="form-control rounded-1 shadow-none" id="email" placeholder="Enter your email address" style="background-color: rgba(28, 28, 30, 1);" v-model="email" required autocomplete="username">
                
                <!-- Email error message -->
                <span v-if="!isEmailValid" style="color:red; font-size:0.7rem;">Invalid email address</span>
            </div>

            <!-- Password input field -->
            <div class="mb-3">
                <label class="form-label bluecolor" style="font-size:0.8rem;">Password</label>
                <div class="row d-flex m-0">
                    <div class="col-10 p-0 m-0">
                        <input :type="inputType" class="form-control shadow-none" id="password" placeholder="Enter your password" style="background-color: rgba(28, 28, 30, 1);" :maxlength="15" v-model="password" required autocomplete="current-password">
                    </div>
                    <div id="eye" class="col-2 pt-1 m-0 text-center rounded-end focus-ring focus-ring-primary">
                        <img :src="inputTypeIcon" @click.prevent="ToggleInput"/>
                    </div>
                </div>
                
                <!-- Password error msg -->
                <span v-if="!isPasswordValid" style="color:red; font-size:0.7rem;">Invalid password</span>
                <div class="text-end mt-1">
                    <a href="" @click.prevent="forgetPassword()">Forgot Password?</a>
                </div>
            </div>
            
            <div class="mb-3 form-check">
                <input type="checkbox" class="form-check-input rounded-1 p-2" id="checkbox">
                <label class="form-check-label ps-1" style="font-size:0.7rem; color:rgba(188, 188, 188, 1);">Keep me signed in for 30 days</label>
            </div>

            <!-- Sign-In Button -->
            <button type="submit" class="form-control btn btn-primary rounded-1 my-4"><span style="font-size:0.9rem;">SIGN IN</span></button>
        </form>

        <!-- Terms and services section -->
        <div class="">
                <a href="">Read our Terms of Service <img class="ms-1" id="externalLink" :src="external_logo"/></a>
        </div>
    </div>
</template>


<script>
import Toastify from 'toastify-js';
import 'toastify-js/src/toastify.css';

export default {
  name: 'InputContainer',
  data() {
    return {
        email: '',
        password: '',
        isEmailValid: true,
        isPasswordValid: true,
        inputType:"password",
        external_logo: require('@/assets/Images/External_Link.png'),
        eye_close:require('@/assets/Images/eye-closed.svg'),
        eye_open:require('@/assets/Images/eye-open.svg'),
        inputTypeIcon:require('@/assets/Images/eye-closed.svg'),
        isInputFocused: false
        
    };
  },

  methods:{
    // Form Handling
    submitForm() {
        console.log(this.email);
        console.log(this.password);

        // Validate email and password
        this.isEmailValid = this.isValidEmail(this.email);
        this.isPasswordValid = this.password.length >= 8;

        // Check if both email and password are valid
        if (this.isEmailValid && this.isPasswordValid) {
            // Submit form logic here
            this.showToast();
        } else {
            // Handle form errors
            if (!this.isEmailValid) {
                // Set isEmailValid to false to show error message
                this.isEmailValid = false;
            }
            if (!this.isPasswordValid) {
                // Set isPasswordValid to false to show error message
                this.isPasswordValid = false;
            }
        }
    },

    isValidEmail(email) {
        console.log('Email validation:', email);
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/;
        const isValid = emailRegex.test(email);
        console.log('Is valid email:', isValid);
        return isValid;
    },

    // Password-Icon Toggle handling
    ToggleInput(){
        if(this.inputType==="password")
        {
            this.inputType="text";
            this.inputTypeIcon=this.eye_open;
        }
        else
        {
            this.inputType="password";
            this.inputTypeIcon=this.eye_close;
        }
        console.log("Input Type: ", this.inputType);
        console.log("Input Type Icon: ", this.inputTypeIcon);
    },

    addFocusClass() {
            this.isInputFocused = true; // Set the flag to true when input is focused
    },

    removeFocusClass() {
        this.isInputFocused = false;
    },

    // Toastify-PopUp Message
    showToast() {
        Toastify({
        text: "Sign In Successfull",
        duration: 3000, // Duration in milliseconds
        gravity: "top", // 'top' or 'bottom'
        position: 'right', // 'left', 'center', or 'right'
        backgroundColor: "linear-gradient(to right, #00b09b, #96c93d)", // Background color
        }).showToast();
    },

    forgetPassword()
    {
        alert("Forget Password clicked");
    },

  }
}
</script>

<style>

    #signIn
    {
        font-weight: 600;
    }

    .whitecolor
    {
        color:white;
    }

    .bluecolor
    {
        color:rgba(26, 104, 255, 1);
    }

    input
    {
        border:2px solid rgba(44, 44, 46, 1) !important;
        caret-color: rgba(188, 188, 188, 1);
        color: rgba(188, 188, 188, 1) !important;
        
    }

    #password
    {
        border-right: none !important;
        border-top-right-radius:0 !important;
        border-bottom-right-radius:0 !important;
    }

    #eye
    {
        border:2px solid rgba(44, 44, 46, 1) !important;
        border-top-left-radius:0 !important;
        border-bottom-left-radius:0 !important;
        border-left: none !important;
        background-color: rgba(28, 28, 30, 1);
    }

    #eye img
    {
        width: 1.5rem;
    }

    #eye img:hover
    {
        cursor: pointer;
    }


    a{
        text-decoration: none;
        font-size: 0.7rem;
        color: rgba(188, 188, 188, 1);
    }

    #externalLink
    {
        width:0.8rem;
        height: 0.8rem;
        padding-bottom: 0.09rem;
    }

    button
    {
        letter-spacing: 0.08rem;
    }

    .form-control::placeholder 
    { 
        
        /* Firefox, Chrome, Opera */ 
        color: rgb(188,188,188); 
        font-size: 0.8rem;
    } 
      
    .form-control:-ms-input-placeholder
    { 
        
        /* Internet Explorer 10-11 */ 
        color: rgb(188,188,188);
        font-size: 0.8rem;
    } 

    .form-check-input
    {
        background-color: transparent;
        border:1.5px solid rgba(188, 188, 188, 1) !important;
    }
    
    input:-webkit-autofill
    { 
        -webkit-box-shadow: 0 0 0 1000px rgba(28, 28, 30, 1) inset !important;
        -webkit-text-fill-color: rgba(188, 188, 188, 1) !important;
    }
    
    input:-webkit-autofill:focus { 
        -webkit-box-shadow: 0 0 0 1000px rgba(28, 28, 30, 1) inset !important;
        -webkit-text-fill-color: rgba(188, 188, 188, 1) !important;
    }

</style>
