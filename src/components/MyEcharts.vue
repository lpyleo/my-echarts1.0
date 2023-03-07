<template>
    <div :id="uuid" :style="style"></div>
</template>

<script>
import * as echarts from 'echarts'
import { v4 as uuidv4 } from 'uuid';

const uuid = uuidv4()

export default {
    props: {
        height: {
            type: String,
            default: '400px'
        },
        width: {
            type: String,
            default: '600px'
        },
        options: {
            type: Object,
            default: null
        }
    },
    data() {
        return {
            uuid: null,
            myChart: null
        }
    },
    watch: {
        width() {
            if (this.myChart) {
                this.$nextTick(() => {
                    this.myChart.resize({
                        animation: {
                            duration: 300
                        }
                    })
                })
            }
        },

        options() {
            if (this.myChart) {
                this.$nextTick(() => {
                    this.myChart.setOption(this.options, {
                        notMerge: true
                    });
                })
            }
        }
    },
    computed: {
        style() {
            return {
                height: this.height,
                width: this.width
            }
        }
    },
    created() {
        this.uuid = uuid
    },
    mounted() {
        // 基于准备好的dom，初始化echarts实例
        this.myChart = echarts.init(document.getElementById(this.uuid))

        // 使用刚指定的配置项和数据显示图表。
        this.myChart.setOption(this.options);
    }
}
</script>

<style></style>