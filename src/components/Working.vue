<template>
    <div>
        <div class="tab-content">
            <ul class="working-list">
                <li class="schedule">
                    <div>Schedule</div>
                    <div class="checkboxes">
                        <div class="checkbox">
                            <label v-bind:class="{'active-radio': flex === 'Fixed'}"><input type="radio" value="Fixed" v-model="flex" hidden></label>
                            <span class="checkbox-title"> Fixed</span>
                        </div>
                        <div class="checkbox">
                            <label  v-bind:class="{'active-radio': flex === 'Flexible'}" ><input type="radio" value="Flexible" v-model="flex" hidden></label>
                            <span class="checkbox-title"> Flexible</span>
                        </div>
                    </div>
                </li>
                <li v-for="item in week">
                    <div><input v-if="typeof item.checkbox === 'boolean'" type="checkbox" class="checkbox-item" v-model="item.checkbox">{{ item.day }}</div>
                    <vue-range-slider v-bind:check="item.checkbox === false ? false : true" v-bind:startvalue="item.startvalue" v-bind:max="1440"></vue-range-slider>
                </li>
            </ul>
        </div>
        <div class="tab-footer">
            <button class="save">SAVE CHANGES</button>
            <span class="cancel">Cancel</span>
            <span class="reset">to reset changes</span>
        </div>
    </div>
</template>

<script>
    import VueRangeSlider from "./VueRangeSlider";
    export default {
        name: 'Working',
        components: {
            VueRangeSlider,
        },
        data(){
            return {
                flex: 'Fixed',
                week: [
                    { day: "Working hours", startvalue: [480, 1020], checkbox: ''},
                    { day: "Monday", startvalue: [480, 1020], checkbox: true},
                    { day: "Tuesday", startvalue: [480, 1020], checkbox: true },
                    { day: "Wedndesday", startvalue: [480, 1020], checkbox: true },
                    { day: "Thursday", startvalue: [480, 1020], checkbox: true },
                    { day: "Friday", startvalue: [480, 1020], checkbox: true },
                    { day: "Saturday", startvalue: [480, 1020], checkbox: false },
                    { day: "Sunday", startvalue: [480, 1020], checkbox: false },
                ]
            }
        }
    }
</script>
