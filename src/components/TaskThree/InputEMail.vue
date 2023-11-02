<template>
    <div class="mail__body">
        <label class="mail__label">
            Введіть e-mail:
            <input v-model="auditMailAddress" type="email" :class="['mail__input', colorInputDomain]" />
        </label>
    </div>
</template>

<script>
export default {
    name: 'InputEMail',
    props: {
        modelValue: {
            type: String,
        },
    },
    data() {
        return {
            colorAddressMail: null,
        }
    },
    computed: {
        auditMailAddress: {
            get() {
                return this.modelValue
            },
            set(userMail) {
                userMail = this.addDomain(userMail)
                this.$emit('update:modelValue', userMail)
            },
        },

        colorInputDomain() {
            return this.colorAddressMail
        },
    },
    methods: {
        addDomain(userMail) {
            this.checkDomain(userMail)
            if (userMail.match(/@$/g)) {
                userMail = userMail + 'inv.mn.edu'
                this.colorAddressMail = 'color__true-domain'
            }
            return userMail
        },
        checkDomain(userMail) {
            if (userMail.match(/@/g)) {
                if (userMail.match(/@inv\.mn\.edu$/g) !== null) this.colorAddressMail = 'color__true-domain'
                else this.colorAddressMail = 'color__wrong-domain'
            }
        },
    },
}
</script>

<style lang="scss" scoped>
.color__wrong-domain {
    background-color: rgba(233, 27, 0, 0.603);
}
.color__true-domain {
    background-color: white;
}
</style>
