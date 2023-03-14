<template>
    <div>
        <div class="h-1/3 flex items-center justify-center">
            <h1 class="poppins font-bold text-xl"> Sign Up </h1>
        </div>

        <div class="w-full lg:w-1/3 mx-auto" v-if="signup">
            <input 
            v-model="firstname"
            class="bg-gray-200 rounded-full p-3 block mb-4 w-full"
            placeholder="enter your firstname"
            type="text"
            />

            <input 
            v-model="lastname"
            class="bg-gray-200 rounded-full p-3 block mb-4 w-full"
            placeholder="enter your lastname"
            type="text"
            />

            <input 
            v-model="email"
            class="bg-gray-200 rounded-full p-3 block mb-4 w-full"
            placeholder="enter your email"
            type="email"
            />
    
            <input 
            v-model="password"
            class="bg-gray-200 rounded-full p-3 block mb-4 w-full"
            placeholder="enter a password"
            type="password"
            />
    
            <div class="flex justify-between mulish mt-6">
                <button
                class="py-2 px-4 text-black/70 rounded-full mr-2"
                @click="login"
                >
                    Log In
                </button>

                <button
                class="py-2 px-4 bg-blue-100 text-blue-700 font-bold rounded-full"
                @click="next"
                >
                    Next
                </button>
            </div>
        </div>

        <div class="w-full md:w-1/3 mx-auto" v-else>
            <p class="p-3">
                a code sent to <span class="px-[.4rem] py-1 rounded bg-blue-100 text-blue-700">{{ email }}</span>, please enter it below.
            </p>
            <p class="mb-4 p-3">
                wrong email? <span class="text-blue-700 underline cursor-pointer" @click="change">change</span>
            </p>

            <input 
            v-model="code"
            class="bg-gray-200 rounded-full p-3 block mb-4 w-full"
            placeholder="enter verification code"
            type="text"
            />
    
            <div class="flex justify-between mulish mt-6">
                <button class="py-2 px-4 text-black/70 rounded-full mr-2">
                    Resend Verification Code
                </button>

                <button class="py-2 px-4 bg-blue-100 text-blue-700 font-bold rounded-full">
                    Verify
                </button>
            </div>
        </div>

    </div>
</template>
<script>
export default {
    data() {
        return {
            signup: true,

            code: null,

            email: null,
            password: null,
            firstname: null,
            lastname: null,
        }
    },

    methods: {
        next() {
            this.signup = false
        },

        change() {
            this.signup = true
        },

        verify() {},

        resend() {},

        login() {
            this.$router.push('/login')
        },
    }
}
</script>