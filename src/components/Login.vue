<template>
    <div id="LoginPage" class="row" :style="{ backgroundImage: 'linear-gradient(to right, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.85)), url(' + back_pic + ')' }">
        <div id="Form" class="container d-flex flex-column justify-content-center mx-auto my-auto col-lg-3 col-md-6">
            <div class="flex-grow-1 py-5 px-4">

                <!-- MGM Section -->
                <LogoContainer/>

                <!-- Input Section -->
                <InputContainer/>
            </div>

            <!-- Header Section -->
            <HeaderContainer/>
        </div>
        
    </div>
</template>

<script>

import LogoContainer from './Logo_Container.vue';
import InputContainer from './Input_Container.vue';
import HeaderContainer from './Header_Container.vue';


export default {
    name: 'LoginForm',
    components: {
        LogoContainer,
        InputContainer,
        HeaderContainer
    },
    data(){
        return{
            back_pic: require('@/assets/Images/Netflix-background.jpg')
        }
    }
    
}

</script>

<style>

/* Google Font Family */
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:ital,wght@0,100..900;1,100..900&family=Poppins&display=swap');

    *{
        margin: 0;
        font-family: "Noto Sans", sans-serif;
    }

    #LoginPage 
    {
        height: 100vh;
        background-size: cover;
        gap: 0;
        margin: 0;
    }

    #Form 
    {
        background-color: rgba(9, 9, 9, 1);
        border: 3px solid rgba(24, 24, 24, 1);   
        height: fit-content;
        padding: 0 0 0 0;
    }

    #Form div
    {
        margin: 0px 6px;
    }

</style>
