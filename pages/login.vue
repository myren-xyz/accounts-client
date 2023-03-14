<template>
    <div>
        <div class="h-1/3 flex items-center justify-center">
            <h1 class="poppins font-bold text-xl"> Log In </h1>
        </div>

        <div class="w-full lg:w-1/3 mx-auto">
            <input 
            v-model="email"
            class="bg-gray-200 rounded-full p-3 block mb-4 w-full"
            placeholder="enter your email"
            />
    
            <input 
            v-model="password"
            class="bg-gray-200 rounded-full p-3 block mb-4 w-full"
            placeholder="enter your password"
            />
    
            <div class="flex justify-between mulish mt-6">
                <button
                class="py-2 px-4 text-black/70 rounded-full mr-2"
                @click="signup"
                >
                    Sign Up
                </button>

                <button class="py-2 px-4 bg-blue-100 text-blue-700 font-bold rounded-full">
                    Log In
                </button>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            email: null,
            password: null,
        }
    },

    methods: {
        login() {},
        
        signup() {
            this.$router.push('/signup')
        },
    }
}
</script>