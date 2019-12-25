<template>
    <div id="sync-child-div">
        我是儿子，我知道我爸爸有这么些钱：<span class="data">{{money}}</span>
        <button @click="$emit('update:money',money-100)">我要花一百块</button>
    </div>
</template>

<script>
export default {
    props:['money']
}
</script>

<style lang="scss">
#sync-child-div{
    border: 1px solid orange;
    padding: 10px;
}
</style>