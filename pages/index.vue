<template>
    <div>
        <div class="container" :class="{'register-active' : register_view}">

            <div class="overlay-container">

                <Notification :message="error" v-if="error"/>

                <div class="overlay">
                    <div class="overlay-left">

                        <h2>Welcome Back!</h2>
                        <p>Please login with your account</p>
                        <button class="invert" id="logIn" @click="register_view = !register_view">Login</button>

                    </div>

                    <div class="overlay-right">

                        <h2>Hello Friend!</h2>
                        <p>Please enter your personal details</p>
                        <button class="invert" id="regis" @click="register_view = !register_view">Register</button>

                    </div>
                </div>

            </div>

            <form class="register_view" method="post" @submit.prevent="register">

                <h2>Create Account</h2>
                <div>Use your email for registration</div>
            <div class="field">
              
              <div class="control">
                <input
                  type="text"
                  class="input"
                  name="name"
                  v-model="name"
                  required
                  placeholder="Full Name"
                >
              </div>
            </div>
            <div class="field">
              
              <div class="control">
                <input
                  type="text"
                  class="input"
                  name="username"
                  v-model="username"
                  required
                  placeholder="Username"
                >
              </div>
            </div>
            <div class="field">
              
              <div class="control">
                <input
                  type="email"
                  class="input"
                  name="email"
                  v-model="email"
                  required
                  placeholder="Email"
                >
              </div>
            </div>
            <div class="field">
              
              <div class="control">
                <input
                  type="password"
                  class="input"
                  name="password"
                  v-model="password"
                  required
                  placeholder="Password"
                >
              </div>
            </div>
                <!-- <button>Register</button> -->
                <div class="control">
                    <button type="submit" class="button is-fullwidth">Register</button>
                </div>
            </form>

            <!-- <form class="login_view" action="#"> -->
            <form class="login_view" method="post" @submit.prevent="login">
                <h2>Login</h2>
                <div>Enter your account details</div>

                <div class="field">
                    <div class="control">
                        <input
                        type="username"
                        class="input"
                        name="username"
                        v-model="username"
                        >
                    </div>
                </div>
                <div class="field">
                    <div class="control">
                        <input
                        type="password"
                        class="input"
                        name="password"
                        v-model="password"
                        >
                    </div>
                </div>
                <a href="#">Forgot Password?</a>
                
                <div class="control">
                    <button type="submit" class="button is-fullwidth">Log In</button>
                </div>

            </form>

        </div>
    </div>
</template>

<script>
import Notification from '~/components/Notification'

    export default {
        components: {
            Notification,
        },
        data: () => {
            return{
                register_view: false,

                name: '',
                username: '',
                email: '',
                password: '',
                error: null
            }
        },
        middleware: 'guest',

        methods: {
            async register() {
                try {
                    await this.$axios.post('register/', {
                        name: this.name,
                        username: this.username,
                        email: this.email,
                        password: this.password
                    })

                    await this.$auth.loginWith('local', {
                    data: {
                        username: this.username,
                        password: this.password
                    },
                    })

                    this.$router.push('/list')
                } catch (e) {
                    this.error = e.response.data.message
                }
            },
            async login() {
                try {
                    await this.$auth.loginWith('local', {
                        data: {
                            username: this.username,
                            password: this.password
                        }
                    })

                    this.$router.push('/list')
                } catch (e) {
                    this.error = e.response.data.message
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

    article {
      // min-height: 100vh;
      background-image: linear-gradient(
          to right,
          rgba(0, 0, 0, 0.9),
          rgba(0, 0, 0, 0.89)
        ),
        url("/images/banner.jpg");
      background-position: center;
      background-size: cover;
      position: relative;
    }

    .container {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        // position: relative;
        width: 768px;
        height: 480px;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 15px 30px rgba(0,0,0,.2),
                    0 10px 30px rgba(0,0,0,.2);
        background: linear-gradient(to bottom, #efefef, #ccc);
        
        .overlay-container {
            position: absolute;
            top: 0;
            left: 50%;
            width: 50%;
            height: 100%;
            overflow: hidden;
            transition: transform .5s ease-in-out;
            z-index: 100;
        }

        .overlay {
            position: relative;
            left: -100%;
            height: 100%;
            width: 200%;
            background: linear-gradient(to bottom right, rgba(236, 82, 177, 0.692), rgba(185, 46, 155, 0.973));
            color: #fff;
            transform: translateX(0);
            transition: transform .5s ease-in-out;
        }

        @mixin overlays($property) {
            position: absolute;
            top:60px;
            display: flex;
            align-items: center;
            justify-content: space-around;
            flex-direction: column;
            padding: 70px 40px;
            width: calc(50% - 80px);
            height: calc(100% - 140px);
            text-align: center;
            transform: translateX($property);
            transition: transform .5s ease-in-out;
        }
        .overlay-left {
            // @include overlays(0);
            // left: 0;
            position: absolute;
            // top:0;
            display: flex;
            align-items: center;
            justify-content: space-around;
            flex-direction: column;
            padding: 70px 40px;
            width: calc(50% - 80px);
            height: calc(100% - 140px);
            text-align: center;
            transform: translateX(-200%);
            transition: transform .5s ease-in-out;
            left: 5%;
        }

        .overlay-right {
            @include overlays(0);
            right: 5%;

        }
    }

    h2 {
        margin: 0;
        font-size: 2em;
    }

    p {
       margin: 20px 0 30px; 
    }

    a {
        color: #222;
        text-decoration: none;
        margin: 15px 0;
        font-size: 1rem;
    }

    button {
        border-radius: 20px;
        border: 1px solid;
        background-color: rgba(236, 82, 177, 0.692);
        color: #fff;
        font-size: 1rem;
        font-weight: bold;
        padding: 10px 40px;
        letter-spacing: 1px;
        text-transform: uppercase;
        transition: transform .1s ease-in;

        &:active {
            transform: scale(.9);
        }

        &:hover {
            border: none;
        }
    }

    button.invert {
        background-color: transparent;
        border-color: #fff;

    }

    form {
        position: absolute;
        top: 0;
        display: flex;
        align-items: center;
        justify-content: space-around;
        flex-direction: column;
        padding: 10px;
        width: calc(50% - 120px);
        height: calc(100% - 180px);
        text-align: center;
        // background: linear-gradient(to bottom, #efefef, #ccc);
        transition: all .5s ease-in-out;

        div {
            font-size: 1rem;
        }

        input {
            background-color: #eee;
            border: none;
            padding: 15px;
            margin-top: 10px;
            width: 100%;
            border-radius: 15px;
            border-bottom: 1px solid #ddd;
            box-shadow: inset 0 1px 2px rgb(0, 0, 0, .4),
                        0 -1px 1px #fff,
                        0 1px 0 #fff;
            overflow: hidden;

            &:focus {
                outline: none;
                background-color: #fff;
                border-radius: 15px;
            }
        }
    }

    .login_view {
        left: 60px;
        top: 60px;
        z-index: 2;
    }

    .register_view {
        right: 60px;
        top: 60px;
        z-index: 1;
        opacity: 0;
        animation: show .5s;
    }

    .register-active {
        .login_view {
            transform: translateX(0%);
            opacity: 0;
        }

        .register_view {
            transform: translateX(0%);
            opacity: 1;
            z-index: 5;
        }

        .overlay-container {
            transform: translateX(-100%);
        }

        .overlay {
            transform: translateX(50%);
        }

        .overlay-left {
            transform: translateX(0);
        }

        .overlay-right {
            transform: translateX(20%);
        }
    }

    @keyframes show {
        0% {
            opacity: 0;
            z-index: 1;
        }
        49% {
            opacity: 0;
            z-index: 1;
        }
        50% {
            opacity: 1;
            z-index: 10;
        }
    }


</style>