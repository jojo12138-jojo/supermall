<template>
    <div class="tab-control">
        <div v-for="(item, index) in titles" :key="index"
             class="tab-control-item"
             :class="{active: index === activeindex}"
             @click="activeclick(index)">
            <span>{{item}}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Tabcontrol',
    props: {
        titles: {
            type: Array,
            default() {
                return []
            }
        }
    },
    
    methods: {
        activeclick(index) {
            this.activeindex = index;
            this.$emit('tabClick', index)
        }
    },
    data() {
        return {
            activeindex: 0
        }
    },
}
</script>

<style scoped>
    .tab-control {
        display: flex;
        text-align: center;
        font-size: 15px;
        height: 40px;
        line-height: 40px;
        background-color: #fff;
    }

    .tab-control-item {
        flex: 1;
    }

    .tab-control-item span {
        padding: 5px;
    }
    
    .active {
        color: var(--color-high-text);
    }
    .active span {
        border-bottom: 3px solid var(--color-tint);
    }
</style>