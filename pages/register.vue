<template>
<v-row class="fixed-h">
    <v-col md="5" sm="12" style="padding:0">
        <div class="login-banner">
            <div class="bottom-block">
                <div class="logos d-flex align-center">
                    <img src="../assets/img/logo.svg">

                    <img src="../assets/img/everfit_wordmark.png">
                </div>
                <p>Creating and managing your clients is easy as 1-2-3. Easily invite the clients you want to connect through the platform and start training.
                </p>
            </div>
        </div>
    </v-col>
    <v-col md="7" sm="12" style="padding:0">
        <div class="reg-block">
           <reg v-if="$route.name == 'register'"/>
           <lognicom v-if="$route.name == 'login'"/>
        </div>
    </v-col>
</v-row>
</template>

<script>
import reg from '../components/sign'
import lognicom from '../components/login'

export default {
    components:{
        reg,
        lognicom
    },
    data() {
        return {
            valid: false,
            email: '',
            pass: '',
            usertype: 0,
            notreg: false
        }
    },
    methods: {
        choosetype(type) {
            this.usertype = type;
        },
        register() {
            this.notreg = true;
        }
    },
    mounted(){
        console.log(this.$route.name)
    }
}
</script>

<style lang="scss">
.fixed-h {
    height: 100vh;

    .login-banner {
        height: 100%;
        width: 100%;
        background-image: url('../assets/img/left-banner.jpg');
        background-size: cover;
        position: relative;
        background-blend-mode: overlay;
        background-color: rgb(0 0 0 / 15%);

        .bottom-block {
            position: absolute;
            bottom: 18px;
            left: 50px;

            p {
                color: #fff;
            }

            .logos {
                margin-bottom: 10px;
            }

            img {
                &:first-of-type {
                    width: 25px;
                    margin-right: 10px;
                }

                width: 100px;
                object-fit: cover;
            }
        }

        img {
            height: 100%;
            width: 100%;
        }
    }
}

.reg-block {
    background-color: #f8f8f8;
    height: 100%;
    width: 100%;
    padding-top: 4rem;

    .sign-form {
        background-color: #fff;
        width: 55%;
        margin: 1rem auto;
        padding: 1rem 2rem;
        border-radius: 10px;
        box-shadow: rgb(73 70 153 / 10%) 0px 2px 4px;
        text-align: center;

        .myform {
            padding: 2rem 1rem;

            .mysumbit {
                margin: 2rem 0;
                padding: 15px 4rem;
            }
        }
    }
}
</style>
