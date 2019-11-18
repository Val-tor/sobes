<template>
    <div class="slyder" v-if="check">
        <div class="time">
            <div class="time-start">
                {{getTime(value[0])}}
            </div>
            <div class="time-end">
                {{getTime(value[1])}}
            </div>
        </div>
        <vue-range-slider
                :bg-style="{backgroundColor: '#d8d8d8'}"
                :max="max"
                height="8"
                :process-style="{backgroundColor: '#990000'}"
                :tooltipStyle="{display: 'none'}"
                width="100%"
                v-model="value"/>
    </div>
</template>
<script>
    import 'vue-range-component/dist/vue-range-slider.css'
    import VueRangeSlider from 'vue-range-component'

    export default {
        data(){
            return{
                value: this.startvalue,
            }
        },
        methods: {
            getTime(time){
                let hours = Math.floor(time/60);
                let min = time % 60;
                return `${hours >= 10 ? hours : ('0' + hours)}:${min >= 10 ? min : '0' + min}`;
            },
        },
        props: ['max', 'startvalue', 'check'],
        components: {
            VueRangeSlider
        }
    }
</script>