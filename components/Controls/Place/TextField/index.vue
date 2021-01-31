<template>
  <div>
      <p class="label">{{label}}</p>
      <input type="text" v-model="value" :placeholder="placeholder" :class="inputClass">
      <p class="warning" :class="warningClass">{{warning.value}}</p>
  </div>
</template>

<script>
export default {
    props: ['label', 'placeholder', 'block', 'warning'],
    computed: {
        inputClass() {
            return {
                'block': this.block
            }
        },

        warningClass() {
            return {
                'hide': !this.warning.status
            }
        },

        value: {
            get() {return this.text},

            set(val) {
                this.text = val;
                this.$emit('filter', val);
            }
        } 
    },
    data() {
        return {
            text: ''
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
    input {
        background: #FFFFFF;
        border: 1px solid #DBE2EA;
        box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
        border-radius: 6px;
        padding: 16px;
        font-size: 16px;
        transition: border-color .1s;

        &:focus {border-color: #459FC2;}
        &::placeholder {color: #7C9CBF;}
    }

    .warning {
        color: #FF7171;
        font-size: 14px;
        margin-top: 3px;
    }

    .block {width: 100%;}

    .hide {opacity: 0;}
</style>