<template>
    <form class="">
        <Title :text="title" />
        <Subtitle :text="subtitle" />
        <div v-for="item in items" :key="item.index" class="my-3" >
            {{item.name}}
            <span><input v-model="item.model" class="input" :type="item.type"></span>
        </div>
        <button class="button" @click.prevent.stop="SendData()">
            {{action}}
        </button>
    </form>
</template>

<script>
export default {
    props: {
        title: {
            type: String,
            default: ""
        },
        subtitle: {
            type: String,
            default: ""
        },
        action: {
            type: String,
            default: ""
        }
    },
    data() {
        return {
            items: [
            {
                name: "E-mail",
                value: "email",
                type: "text",
                model: ""
            },
            {
                name: "Senha",
                value: "password",
                type: "password",
                model: ""
            }
        ]
        }
    },
    methods: {
        SendData () {
            const data = {};
            // mapping the data to send for login or sign in
            this.items.map((i) => {
                data[i.value] = i.model;
            });
            // emmiting evvent with user data
            this.$emit("SendData", data)
        }
    },

}
</script>

<style>

</style>