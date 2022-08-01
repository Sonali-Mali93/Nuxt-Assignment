<template>
    <div>
        <div class="flex mb-4 space-x-2">
            <div v-for="per in times" :key="per" class="w-1/4 bg-gray-500">
                <p>Start Time -{{ per.tt }}</p>
                <p>End Time -</p>
                <button class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white" type="submit"
                    value="Submit"> Book Now</button>
            </div>
            <div class="w-1/4 bg-gray-400 h-12">
            </div>
            <div class="w-1/4 bg-gray-500 h-12">
            </div>
            <div class="w-1/4 bg-gray-400 h-12">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            intervals: 10,
            i: 0,
            times: [],
            tt: 0,
            ap: ['AM', 'PM'],
            timeslots: {
                startTime: '',
                endTime: ''
            }
        }

    },
    methods: {
        addslots() {
            for (i = 0; tt < 24 * 60; i++) {
                var hh = Math.floor(tt / 60); // getting hours of day in 0-24 format
                var mm = (tt % 60); // getting minutes of the hour in 0-55 format
                times[i] = ("0" + (hh % 12)).slice(-2) + ':' + ("0" + mm).slice(-2) + ap[Math.floor(hh / 12)]; // pushing data in array in [00:00 - 12:00 AM/PM format]
                tt = tt + x;
                console.log(tt)
            }
        }
    }
}

</script>