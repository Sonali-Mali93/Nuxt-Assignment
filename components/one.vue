<template>
    <div>        
        <div @click="addSlots()" class=" openForm flex mb-4 space-x-2 text-3xl font-bold bg-pink-400 ">click Here to see the
            available time slots</div>

             <form  v-if="flag==true" @submit="submitForm" class="px-4 my-10 max-w-3xl mx-auto space-y-3 drop-shadow-md"
            method="post">
            <h1 class="text-3xl font-semibold">Book the slots</h1>
            <hr class="bg-black">
            <div class="flex space-x-4">
                <div class="w-1/2">
                    <label for="Name">Name:</label>
                    <input v-model="user.firstName"
                        class="border border-gray-400 block px-4 py-1 w-full rounded focus:outline-none focus:border-teal-500"
                        type="text" name="firstname" id="firstname" required>
                </div>
                <div class="w-1/2">
                    <label for="Name">Mobile No:</label>
                    <input v-model="user.contact"
                        class="border border-gray-400 block px-4 py-1 w-full rounded focus:outline-none focus:border-teal-500"
                        type="text" name="contact" id="contact" required>
                </div>
            </div>
            <div class="form_action_button space-x-2">
                <button class="border border-gray-400 px-4 py-2 max-w-xs rounded bg-teal-600 text-white" type="submit"
                    value="Submit">Submit</button>
            </div>
        </form>
        <div v-for="(per, index) in users" v-bind:index="index" :key="per" class="flex flex-wrap -mb-4 ">
            <div class="w-1/3 mb-4 bg-red-400 space-y-4">
                <p>Name - {{ per.firstName }}</p>
                <p>Mobile No - {{ per.contact }}</p>
                <button @click="editData(index)"
                    class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white" type="submit"
                    value="Submit"> Edit Details</button>
            </div>
        </div>  


        <div class="flex flex-wrap flex-row space-y-3">
        <div v-for="(per) in timeSlots" :key="per" >
            <!---main card div-->
            <div class="max-w-sm rounded overflow-hidden ">
                <div class="px-6 py-4">
                    <div class="font-bold text-xl mb-2">Start Time - {{ per.startTime }}</div>
                    <div class="font-bold text-xl mb-2">Last Time - {{ per.endTime }}</div>
                    <div class="font-bold text-xl mb-2"></div>

                </div>
                <div class="px-6 pt-4 pb-2">
                    <button @click="showForm" class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white ">Book Now
                    </button>
                </div>
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
            i: 0,
            flag:false,
            users: [],
            user: {
                isEdit: true,
                editIndex: -1,
                firstName: '',
                contact: ''
            }
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
        },
        submitForm(event) {
            event.preventDefault();
            if (this.isEdit == true) {
                this.users[this.editIndex] = this.user;
                this.isEdit = false;
                this.editIndex = -1;
            } else {
                this.users.push(this.user);
            }
            this.user = {
                firstName: "",
                contact: "",
            }
            console.log(this.users)
        },
        deleteData(index) {
            if (confirm('You Want To Delete The Data ?'))
                this.users.splice(index, 1);
        },
        editData(index) {
            if (confirm('Do you want to edit data?'))
                console.log("users = ", this.users[index].firstName)
            this.user.firstName = this.users[index].firstName;
            this.user.contact = this.users[index].contact;
            this.isEdit = true;
            this.editIndex = index;
        },
        showForm(){
            this.flag = true
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

