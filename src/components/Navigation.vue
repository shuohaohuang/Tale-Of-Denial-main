<!-- eslint-disable vue/require-v-for-key -->
<template>
    <ul class="navigation-list">
        <li v-for="nav in spaces">
            <button @click="SendSpace(nav)">{{ nav }}</button>
        </li>
    </ul>
</template>

<script>
export default {
    name: "Navigation-header",
    props: {
        spaces: Array
    },
    methods: {
        SendSpace(status) {
            this.$emit("ChangePage", status);
        }
    }
}
</script>

<style scoped>
.navigation-list {
    display: flex;
    flex-grow: 1;
    justify-content: space-between;
    flex-wrap: nowrap;
    align-items: center;
    height: 100%;
}

li {
    list-style-type: none;
    height: 100%;
    flex: 1;
}
button{
    margin-left: 1%

}
</style>