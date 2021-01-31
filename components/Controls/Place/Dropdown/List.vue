<template>
    <transition name="fade" v-if="active">
        <div class="list">
            <div class="item" 
                v-for="item in list"
                :key="item.value"
                @click="$emit('change', item.value)">
                {{item.value}}
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    props: ['list', 'active'],
}
</script>

<style lang="scss" scoped>
    .list {
        position: absolute;
        width: 100%;
        top: 100%; left: 0;
        box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
        border-radius: 6px;
        background: white;
        border: 1px solid #DBE2EA;
        transform: translateY(5px);
        z-index: 1;
    }

    .item {
        padding: 16px 10px;
        font-size: 16px;
        color: #7C9CBF;
        transition: background .05s;

        &:hover {
            background: rgba(#7C9CBF, .15);
        }
    }

    .fade-enter-active, .fade-leave-active {
        transition: all .2s;
    }
    .fade-enter, .fade-leave-to {
        opacity: 0;
        transform: translateY(10px);
    }
</style>