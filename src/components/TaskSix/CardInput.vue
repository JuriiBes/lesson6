<template>
    <from class="card">
        <div class="card__number">
            <label
                >CARD NUMBER<br /><input
                    ref="cardValue"
                    type="text"
                    placeholder="1234-5678-9012-3456"
                    v-model="cardNumb"
            /></label>
        </div>
        <div class="card__date">
            <label class="card__input-date"
                >EXPIRY DATE<br /><input ref="dateValue" type="text" placeholder="MM / YY" v-model="cardDate"
            /></label>
            <label class="card__input-code">SECURE CODE<br /><input type="number" placeholder="* * * " /></label>
        </div>
    </from>
</template>

<script>
export default {
    name: 'CardInput',
    props: {
        cardNumber: {
            type: String,
        },
        cardNumberModifiers: {
            default: () => ({}),
        },
        cardDateExpiry: {
            type: String,
        },
        cardDateExpiryModifiers: {
            default: () => ({}),
        },
    },
    computed: {
        cardNumb: {
            get() {
                return this.cardNumber
            },
            set(newVal) {
                // console.log(this.cardNumberModifiers)
                if (this.cardNumberModifiers.digitsOnly) {
                    newVal = newVal.replace(/\D/g, '')
                    this.$nextTick(() => {
                        this.updateKey++
                        this.$nextTick(() => {
                            this.$refs.cardValue.focus()
                        })
                    })
                }
                if (this.cardNumberModifiers.separate4Digits) {
                    newVal = newVal.replace(/(\d{4}(?=.+))/g, '$1-')
                }
                this.$emit('update:cardNumber', newVal)
            },
        },
        cardDate: {
            get() {
                return this.cardDateExpiry
            },
            set(newVal) {
                if (this.cardDateExpiryModifiers.digitsOnly) {
                    newVal = newVal.replace(/\D/g, '')
                    this.$nextTick(() => {
                        this.updateKey++
                        this.$nextTick(() => {
                            this.$refs.dateValue.focus()
                        })
                    })
                }
                if (this.cardDateExpiryModifiers.separate2Digits) {
                    newVal = newVal.replace(/(\d{2}(?=.+))/g, '$1/')
                }
                this.$emit('update:cardDateExpiry', newVal)
            },
        },
    },
}
</script>

<style lang="scss" scoped>
.card {
    display: flex;
    flex-direction: column;
    row-gap: 15px;
    text-align: start;
    max-width: 350px;
    // .card__number
    &__number {
        & input {
            padding: 5px;
            width: 100%;
        }
    }
    // .card__date
    &__date {
        display: flex;
        text-align: start;
        justify-content: space-between;
    }
    // .card__input-date
    &__input-date {
        flex: 0 0 55%;
        & input {
            width: 100%;
            padding: 5px;
        }
    }
    // .card__input-code
    &__input-code {
        flex: 0 0 35%;
        & input {
            width: 100%;
            padding: 5px;
        }
    }
}
</style>
