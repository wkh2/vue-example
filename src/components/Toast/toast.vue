<template>
    <div v-if="visible">
        <div class="toast-mask-transparent"></div>
        <div class="toast"  :class="customClass">
            {{message}}
        </div>
    </div>
</template>
<script>
export default {
    props: {
        message: String
    },
    data() {
        return {
            visible: false
        };
    },
    computed: {
        customClass() {
            var classes = [];
            switch (this.show) {
                case 'true':
                    classes.push('toast__show');
                    break;
                case 'false':
                    classes.push('toast__hide');
                    break;
                default:
                    classes.push('');
            }
            classes.push(this.className);

            return classes.join(' ');
        }
    }
}
</script>
<style lang="less" scoped>
.toast-mask {
    position: fixed;
    z-index: 1000;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background: rgba(0, 0, 0, .6);
}

.toast-mask-transparent {
    position: fixed;
    z-index: 1000;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
}

.toast {
    font-size: .24rem;
    position: fixed;
    max-width: 80%;
    border-radius: 5px;
    background: rgba(0, 0, 0, 0.7);
    color: #fff;
    box-sizing: border-box;
    text-align: center;
    z-index: 1000;
    padding: .2rem .4rem;
    transition: opacity .3s linear;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

.toast__show {
    opacity: 1;
}

.toast__hide {
    opacity: 0;
}
</style>
