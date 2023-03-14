<template>
    <div>
        <p> hello world </p>
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
        ctx.store.commit('UPDATE_USER', user)
    }
}
</script>