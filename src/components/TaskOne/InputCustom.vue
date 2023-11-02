<template>
    <div class="custom__body">
        <label class="custom__label">
            Введіть вік користувача:
            <input type="number" :class="['custom__input', ageBackColor]" v-model="ageUser"
        /></label>
        <div v-show="auditCorrectAge">Введіть коректний вік.</div>
    </div>
</template>

<script>
export default {
    name: 'InputCustom',
    props: {
        modelValue: {
            type: Number,
        },
    },
    data() {
        return {
            backColor: null,
            massage: false,
        }
    },
    computed: {
        ageUser: {
            get() {
                return this.modelValue
            },
            set(ageValue) {
                this.ageInputColor(ageValue)
                this.correctAge(ageValue)
                this.$emit('update:modelValue', ageValue)
            },
        },
        ageBackColor() {
            return this.backColor
        },
        auditCorrectAge() {
            return this.massage
        },
    },
    methods: {
        // модифікатор setColor
        ageInputColor(age) {
            if (!age) this.backColor = 'color-white'
            else if (0 >= age || age > 150) this.backColor = 'color-red'
            else if (0 < age && age < 10) this.backColor = 'color-green'
            else if (age <= 21) this.backColor = 'color-yellow'
            else if (21 < age && age <= 150) this.backColor = 'color-orange'
        },
        // модифікатор check
        correctAge(age) {
            if (age) {
                if (0 > age || age > 150) this.massage = true
                else this.massage = false
            } else this.massage = false
        },
    },
}
</script>

<style lang="scss" scoped>
.custom {
    // .custom__body
    &__body {
        margin: 0 auto;
        padding: 8px 10px;
        border: 2px solid black;
        max-width: 500px;
        min-height: 70px;
    }
    // .custom__label
    &__label {
        display: flex;
        flex-wrap: wrap;
        column-gap: 10px;
        padding: 8px 10px;
        border-radius: 5px;
        justify-content: center;
    }
    &__input {
        outline: none;
        padding-left: 5px;
    }
}
.color-green {
    background-color: green;
    border: 2px solid green;
}
.color-orange {
    background-color: orange;
    border: 2px solid orange;
}
.color-yellow {
    background-color: yellow;
    border: 2px solid yellow;
}
.color-white {
    background-color: white;
    border: 2px solid rgb(112, 109, 109);
}
.color-red {
    background-color: red;
    border: 2px solid red;
}
</style>
