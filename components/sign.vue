<template>
<div>
    <div class="sign-form" v-if="notreg == false">
        <h1 class="primary--text">Sign up for Everfit</h1>
        <v-form class="myform" ref="form" v-model="valid" lazy-validation>
            <v-row>
                <v-col md="12">
                    <v-text-field v-model="email" :rules="[ v => !!v || 'Email is required',  v => /.+@.+\..+/.test(v) || 'E-mail must be valid',]" label="Email Address" required></v-text-field>

                </v-col>
                <v-col md="12">
                    <v-text-field v-model="pass" :rules="[ v => !!v || 'passwrod is required']" label="Create Password" required></v-text-field>
                </v-col>
                <v-col md="6">
                    <v-btn elevation="2" color="primary" :outlined="usertype != 0 ? true : false" @click="choosetype(0)">I`m a Coach</v-btn>
                </v-col>
                <v-col md="6">
                    <v-btn elevation="2" color="primary" :outlined="usertype != 1 ? true : false" @click="choosetype(1)">I`m a Client</v-btn>
                </v-col>
                <v-col md="12">
                    <v-btn @click="register" class="mysumbit" x-large color="primary" :disabled="email.length == 0 || pass.length == 0">
                        Sign Up for free <v-icon>mdi-arrow-right</v-icon>
                    </v-btn>
                </v-col>
            </v-row>
            <p>Already have an account? <nuxt-link to="/login">Log In</nuxt-link>
            </p>
        </v-form>
    </div>
    <div class="sign-form thanks primary--test" style="font-size:40px" v-else>
        <div class="mythanks">
            <v-icon color="success" style="font-size:40px">mdi-check-circle</v-icon><br>
            Thank You
        </div>
    </div>
</div>
</template>
<script>
export default {
    data(){
        return{
            notreg:false,
            email:'',
            pass:'',
            usertype:0,
        }
    }
}
</script>
