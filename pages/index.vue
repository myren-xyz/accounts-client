<template>
    <div>
        <div>
            <div class="rounded-full w-16 h-16 bg-gradient-to-br from-gray-800 to-slate-600 mx-auto m-3 flex items-center justify-center">
                <p class="text-white mulish font-bold">
                    {{ user.firstname[0] }} {{ user.lastname[0] }}
                </p>
            </div>
        </div>
        <h1 class="text-xl poppins text-center">
            Welcome, {{ user.firstname }} {{ user.lastname }}
        </h1>

        <hr class="my-5"/>
    </div>
</template>

<script>
export default{
    name: 'IndexPage',

    asyncData({ redirect, req }) {
        if (!req.headers.cookie) {
            redirect('/login')
            return
        }
        
        const token = req.headers.cookie.replace(
            /(?:(?:^|.*;\s*)MYREN_TOKEN\s*\=\s*([^;]*).*$)|^.*$/,
            '$1'
        )

        if (token == "") {
            redirect('/login')
            return
        }

        // token split by .
        const payload = token.split('.')[1]
        const decoded = Buffer.from(payload, 'base64').toString('ascii')
        const user = JSON.parse(decoded)

        // update user
        return {
            user
        }
    }
}
</script>