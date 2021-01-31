<template>
    <label>
        <input v-model="checked" type="checkbox" class="checkbox">
        <div class="preview"></div>
        <span v-html="label"></span>
    </label>
</template>

<script>
export default {
    props: ['label'],
    computed: {
        checked: {
            get() {return},
            set(val) {
                this.$emit('checked', val)
            }
        }
    }
}
</script>

<style lang="scss" scoepd>
    .checkbox {
        display: none;

        &:checked + .preview::before {opacity: 1;}
        &:checked + .preview {border-color: #0880AE;}
    }

    .preview {
        background: #FFFFFF;
        border: 1px solid #DBE2EA;
        box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
        border-radius: 4px;
        width: 27px;
        height: 27px;
        position: relative;
        border-color: 1px solid  white;
        transition: all .1s;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 18px;
        margin-right: 8px;

        &::before {
            content: '✓';
            color: #0880AE;
            opacity: 0;
        }

    }

    label {
        user-select: none;
        display: flex;
        align-items: center;
    }

    span {
        color: #756F86;
        font-weight: 500;
        font-size: 14px;
    }
</style>