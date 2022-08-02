<template>
    <div>
        <div @click="addSlots()" class="flex mb-4 space-x-2 text-3xl font-bold bg-pink-400 ">click Here to see the
            available time slots</div>
        <!-- <div v-for="(per) in timeSlots" :key="per" class="flex flex-row border border-black w-1/2 mt-2 ">
            <p class="basis-1/4">Start Time = {{ per.startTime }} </p>
            <p class="basis-1/4">End Time ={{ per.endTime }}</p>
            
            <NuxtLink to="demo" class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white">Book Now
            </NuxtLink>
            <button @click="myFunction()">Book </button>
        </div> -->
        <!-- Cards start -->
        <div v-for="(per) in timeSlots" :key="per" class="flex flex-row space-y-3"> <!---main card div-->
            <div class=" flex flex-col  max-w-sm rounded overflow-hidden shadow-lg">
                <div class="px-6 py-4">
                    <div class="font-bold text-xl mb-2">Start Time -  {{ per.startTime }}</div>
                    <div class="font-bold text-xl mb-2">Last Time - {{ per.endTime }}</div>
                    <div class="font-bold text-xl mb-2"></div>

                </div>
                <div class="px-6 pt-4 pb-2">
                    <button @click="myFunction()" class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white ">Book Now </button>
                </div>
            </div>
        </div>

    </div>
    <!--End of Div-->

</template>
<script>
export default {
    data() {
        return {
            timeSlots: [],
            i: 0
        }
    },
    methods: {
        addSlots() {
            var d1 = new Date('2022-08-02 08:50:00');
            var d2 = new Date('2022-08-02 09:00:00');
            for (let i = 0; i < 20; i++) {
                d1.setMinutes(d1.getMinutes() + 10);
                d2.setMinutes(d2.getMinutes() + 10);
                this.timeSlots.push({
                    startTime: d1.toLocaleTimeString(),
                    endTime: d2.toLocaleTimeString()
                })
            }
            console.log(timeSlots)
        },
        myFunction() {
            let text;
            let Name = prompt("Please enter your name:", "Harry Potter");
            let Mobile = prompt("Please enter your mobile number:", "Harry Potter");
            document.getElementById("demo").innerHTML = text;
        }
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

