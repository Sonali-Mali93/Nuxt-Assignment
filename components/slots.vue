<template>
    <div>
        <div @click="addSlots()" class="flex mb-4 space-x-2 text-3xl font-bold bg-pink-400 ">click Here to see the
            available time slots</div>
        <div v-for="(per) in timeSlots" :key="per" class="flex flex-row border border-black w-1/2 mt-2 ">
            <p class="basis-1/4">Start Time = {{ per.startTime }} </p>
            <p class="basis-1/4">End Time  = {{ per.endTime }}</p>
            <!-- <button class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white" type="submit"
                    value="Submit"><NuxtLink to="./demo.vue">Book Now</NuxtLink> </button> -->
            <NuxtLink to="demo" class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white">Book Now
            </NuxtLink>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            timeSlots: [ ],
            i: 0
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
            var d1 = new Date('2022-08-02 08:50:00');
            // var d2 = new Date('2022-08-02 09:00:00');
            for (let i = 0; i < 20; i++) {
                d1.setMinutes(d1.getMinutes() + 10);
                // d2.setMinutes(d2.getMinutes() + 10);
                this.timeSlots.push({
                    startTime: d1.toLocaleTimeString(),
                    // endTime: d2.toLocaleTimeString()
                })
                // console.log("Current Date and Time =",d1)
                // console.log("Time",d1.toLocaleTimeString())
                // this.timeSlots.push(d1.toLocaleTimeString())
                // this.timeSlots.push(this.initialTime)
                // this.initialTime.startTime = this.timeSlots[index].startTime;
                // this.timeSlots.push(this.initialTime)
            }
            console.log(timeSlots)

            },

            //  addSlots() {
            //     var d;
            //     d = new Date('2022-08-02 09:00:00');
            //     // this.timeSlots.push(this.initialTime);
            //     console.log("timeSlots", this.timeSlots)
            //     for (let i = 0; i < 20; i++) {
            //         d.setMinutes(d.getMinutes() + 10);
            //         // d.getTime()
            //         this.timeSlots[this.startTime] = (d.toLocaleTimeString())
            //         console.log("Start Time",this.startTime )
            //         // this.timeSlots.push(d)
            //         console.log("time", d.toLocaleTimeString())
            //         this.timeSlots.push(this.initialTime);

            //     }
            //     console.log("newtime", this.timeSlots)

            // }
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