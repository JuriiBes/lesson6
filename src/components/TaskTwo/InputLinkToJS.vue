<template>
    <div class="link-js">
        <label class="link-js__label">
            Введіть шлях до файлу *.js:
            <input type="text" :class="['link-js__input', wrongColorLink]" v-model="auditLinkToFile" />
        </label>
    </div>
</template>

<script>
export default {
    name: 'InputLinkToJS',
    props: {
        modelValue: {
            type: String,
        },
    },
    data() {
        return {
            linkBgColor: null,
        }
    },
    computed: {
        auditLinkToFile: {
            get() {
                return this.modelValue
            },
            set(userFile) {
                this.checkPath(userFile)
                this.$emit('update:modelValue', userFile)
            },
        },
        wrongColorLink() {
            return this.linkBgColor
        },
    },
    methods: {
        checkPath(userLink) {
            if (userLink.match(/\.../g)) {
                if (userLink.match(/\.js$/g) !== null) this.linkBgColor = 'link-true'
                else this.linkBgColor = 'link-wrong'
            } else this.linkBgColor = 'link-white'
        },
    },
}
</script>

<style lang="scss" scoped>
.link-js {
    // .link-js__label
    &__label {
    }
    // .link-js__input
    &__input {
        padding-left: 5px;
    }
}

.link-wrong {
    background-color: rgba(233, 27, 0, 0.603);
}
.link-true {
    background-color: greenyellow;
}
.link-white {
    background-color: white;
}
</style>
