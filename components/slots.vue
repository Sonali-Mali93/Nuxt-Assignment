<template>
    <div >
        <div @click="addSlots()" class="flex mb-4 space-x-2 text-3xl font-bold">click Here to see the available time slots</div>
            <div v-for="(per, index) in timeSlots" v-bind:index="index" :key="per" class="flex">
                <p>Start Time -{{ per.startTime }} </p>
                <p>End Time -{{ per.endTime }}</p>
                <button class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white" type="submit"
                    value="Submit"><a href="demo.vu"> Book Now </a></button>
            </div>
        </div>
</template>
<script>
export default {
    data() {
        return {
            timeSlots: [],
            i: 0,
            initialTime: {
                startTime: '',
                endTime: ''
            }
        }
    },
    methods: {
        // addSlots(){
        //     for(i=0 ; i<=20 ; i++){
        //         var s = new Date();
        //         console.log(s)
        //         s.setMinutes(s.getMinutes()+5);
        //     }
        // }
        addSlots() {
            var d;
            d = new Date('2022-08-01 09:00:00');
            for(let i = 0; i<20 ; i++){
             d.setMinutes(d.getMinutes() + 10);
             this.timeSlots.push(d)
            console.log("newtime",d)
            }
            console.log("newtime",this.timeSlots)

        }
    }
}
</script>

<!-- <script>
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

</script> -->