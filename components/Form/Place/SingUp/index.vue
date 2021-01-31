<template>
    <div class="register">
        <h1 class="title">Регистрация</h1>
        <p>Уже есть аккаунт? <a href="#">Войти</a></p>

        <TextField class="mt50"
                :label="'Имя'"
                :placeholder="'Введите ваше имя'"
                :block="true"
                :warning="warnings.name"
                @filter="name"
        />
        <TextField class="mt15"
                :label="'Email'"
                :placeholder="'Введите ваше email'"
                :block="true"
                :warning="warnings.email"
                @filter="email"
        />
        <TextField class="mt15"
                :label="'Номер телефона'"
                :placeholder="'Введите номер телефона'"
                :block="true"
                :warning="warnings.phone"
                @filter="phone"
        />

        <Dropdown @change="selected" class="mt15" :label="'Язык'" :list="list"/>

        <Checkbox @checked="inputChecked" class="mt30" :label="`Принимаю <a href='#'>условия</a> использования`"/>

        <Button class="mt30" :disabled="check" :block="true">Зарегистрироваться</Button>
    </div>
</template>

<script>
import TextField from '@/components/Controls/Place/TextField'
import Dropdown from '@/components/Controls/Place/Dropdown'
import Checkbox from '@/components/Controls/Place/Checkbox'
import Button from '@/components/Controls/Place/Button'

export default {
    components: {
        TextField,
        Dropdown,
        Checkbox,
        Button
    },
    data() {
        return {
            list: [
                {value: 'Русский'},
                {value: 'Английский'},
                {value: 'Китайский'},
                {value: 'Испанский'},
            ],
            warnings: {
                name: {value: 'Введено не корректное значение', status: false},
                email: {value: 'Введено не корректное значение', status: false},
                phone: {value: 'Введено не корректное значение', status: false},
            },
            inputName: false,
            inputEmail: false,
            inputPhone: false,
            checked: false,
            lang: false
        }
    },
    methods: {
        name(value) {
            const filter = value.match(/[^a-zA-Zа-яА-ЯёЁ\-\s]/);

            if (filter || value === '') {
                this.warnings.name.status = true;
                this.inputName = false;
            } else {
                this.warnings.name.status = false;
                this.inputName = true;
            }
        },
        phone(value) {
            const filter = value.match(/[^0-9\-\(\)+]/);
            if (filter || value === '') {
                this.warnings.phone.status = true;
                this.inputPhone = false;
            } else {
                this.warnings.phone.status = false;
                this.inputPhone = true;
            }
        },
        email(value) {
            const filter = /^([A-Za-z0-9_\-\.])+\@([A-Za-z0-9_\-\.])+\.([A-Za-z]{2,4})$/;
            if (!filter.test(value) || value === '') {
                this.warnings.email.status = true;
                this.inputEmail = false
            } else {
                this.warnings.email.status = false;
                this.inputEmail = true;
            }
        },
        inputChecked(val) {
            this.checked = val
        },
        selected(val) {
            console.log(val);
            this.lang = val
        }
    },
    computed: {
        check() {
            if (this.inputName && this.inputEmail && this.inputPhone && this.checked && this.lang)
                return false;
            else return true;
        }
    }
}
</script>

<style lang="scss" scoped>
    .register {
        min-width: 360px;
        width: 460px;
        padding: 30px;
        box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.02),
                    0px 32px 64px rgba(44, 39, 56, 0.04);
        border-radius: 24px;
        background: white;

        .title {
            margin: 10px 0;
        }
    }

    .mt15 {margin-top: 20px;}
    .mt30 {margin-top: 30px;}
    .mt50 {margin-top: 50px;}
</style>