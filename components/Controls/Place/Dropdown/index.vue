<template>
    <div>
        <div class="label">{{label}}</div>
        <div class="dropdown" @click="focus">
            <p>{{lang || 'Язык'}}</p>

            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-down" viewBox="0 0 16 16">
                <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"/>
            </svg>

            <List :list="list" :active="active" @change="changeLang"/>
        </div>
    </div>
</template>

<script>
import List from '@/components/Controls/Place/Dropdown/List'

export default {
    props: ['label', 'list'],
    components: {
        List
    },
    data() {
        return {
            active: false,
            lang: false
        }
    },
    methods: {
        focus() {
            event.target.classList.toggle('active')
            this.active = !this.active;
        },

        changeLang(lang) {
            this.lang = lang
            this.$emit('change', lang);
        }
    }
}
</script>

<style lang="scss" scoped>
    .label {
        color: #756F86;
        font-weight: 500;
        font-size: 14px;
        margin-bottom: 5px;
    }

    .dropdown {
        padding: 16px;
        font-size: 16px;
        box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
        border-radius: 6px;
        border: 1px solid #DBE2EA;
        display: flex;
        justify-content: space-between;
        align-items: center;
        user-select: none;
        position: relative;
        cursor: pointer;
        transition: border-color .1s;

        p {color: #7C9CBF;}
        svg {fill: #7C9CBF;}
    }

    .active {border-color:  #0880AE;}
</style>