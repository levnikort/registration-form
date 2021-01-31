<template>
    <button :class="buttonName"><slot/></button>
</template>

<script>
export default {
    props: ['block', 'disabled'],
    computed: {
        buttonName() {
            return {
                'block': this.block,
                'disabled': this.disabled
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    button {
        color: white;
        font-size: 16px;
        background: #0880AE;
        box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.08), 0px 4px 8px rgba(44, 39, 56, 0.08);
        border-radius: 6px;
        font-weight: 500;
        border: 2px solid #0880AE;
        padding: 18px;
        cursor: pointer;
        transition: box-shadow .3s;

        &:hover {
            box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.08), 0px 24px 48px rgba(44, 39, 56, 0.16);
        }

        &:active {
            border-color: black;
        }
    }

    .block {width: 100%;}

    .disabled {
        background: #DBE2EA;
        border-color: #DBE2EA;
        color: #2C2738;

        &:active {
            border-color: #DBE2EA;
        }
    }
</style>