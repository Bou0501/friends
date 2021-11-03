<template>
    <div class="flex justify-around items-center text-center min-h-screen">
        <div>
            <img :src="'/storage/images/welcome.png'" alt="Friends Welcome" class="w-1/3 mx-auto">
            <div v-if="canLogin">
                <Link href="#" v-if="$page.props.user" class="test-lg text-gray-700 underline">
                    ダッシュボード
                </Link>
                <template v-else>
                    <Link :href="route('login')" class="text-white bg-yellow-500 rounded px-3 py-1 hover:bg-yellow-700 mr-3">
                        ログイン
                    </Link>
                    <Link v-if="canRegister" :href="route('register')" class="text-white bg-yellow-500 rounded px-3 py-1 hover:bg-yellow-700">
                        登録
                    </Link>
                </template>
            </div>

            <p class="mt-10">{{ users }} ユーザ利用しています</p>
        </div>
    </div>
</template>

<script>
    import { defineComponent } from 'vue'
    import { Head, Link } from '@inertiajs/inertia-vue3';

    export default defineComponent({
        components: {
            Head,
            Link,
        },

        props: {
            users: Number,
            canLogin: Boolean,
            canRegister: Boolean,
            laravelVersion: String,
            phpVersion: String,
        }
    })
</script>
