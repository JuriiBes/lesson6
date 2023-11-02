<template>
    <form class="user__data">
        <label for="name-user" class="user__name-label">
            Ім'я користувача:
            <input
                id="name-user"
                @input="$emit('update:nameUser', $event.target.value)"
                type="text"
                :class="['user__name-input', colorNameInput]"
            />
        </label>
        <label for="age-user" class="user__age-label">
            Вік користувача:
            <input
                id="age-user"
                @input="$emit('update:ageUser', $event.target.value)"
                type="number"
                :class="['user__age-input', colorAgeInput]"
            />
        </label>
        <button type="button" class="user__button" @click="auditData()">Enter</button>
    </form>
</template>

<script>
export default {
    name: 'FormNameAgeUser',
    props: {
        nameUser: {
            type: String,
        },
        ageUser: {
            type: Number,
        },
    },
    data() {
        return {
            colorInputName: null,
            colorInputAge: null,
        }
    },
    computed: {
        colorNameInput() {
            return this.colorInputName
        },
        colorAgeInput() {
            return this.colorInputAge
        },
    },
    methods: {
        auditEnterName() {
            if (!this.nameUser) this.colorInputName = 'bg-red'
            else this.colorInputName = 'bg-white'
        },
        auditAgeUser() {
            if (this.ageUser < 18) this.colorInputAge = 'bg-red'
            else this.colorInputAge = 'bg-green'
        },
        auditData() {
            this.auditEnterName()
            this.auditAgeUser()
        },
    },
}
</script>

<style lang="scss" scoped>
.user {
    // .user__data
    &__data {
        display: flex;
        flex-direction: column;
        row-gap: 15px;
        margin: 0 auto;
        max-width: 350px;
        color: #0c73e0;
    }
    // .user__name-label
    // .user__age-label
    &__name-label,
    &__age-label {
        display: flex;
        gap: 15px;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
    }
    // .user__name-input
    // .user__age-input
    &__name-input,
    &__age-input {
        flex: 1 1 auto;
        border: 1px solid yellowgreen;
        padding: 5px;
        max-width: 190px;
    }
    // .user__button
    &__button {
        padding: 5px;
        color: #0c73e0;
        background-color: yellowgreen;
        border: 1px solid yellowgreen;
        font-weight: 600;
        transition: background-color ease 0.3s;
        cursor: pointer;
        &:hover {
            background-color: #fff;
        }
    }
}
.bg-red {
    background-color: red;
}
.bg-white {
    background-color: #fff;
}
.bg-green {
    background-color: greenyellow;
}
</style>
