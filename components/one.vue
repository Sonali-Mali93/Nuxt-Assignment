<template>
    <div>
        <div @click="addSlots()" class=" openForm flex mb-4 space-x-2 text-3xl font-bold bg-pink-400 ">click Here to see
            the
            available time slots</div>

        <form v-if="flag == true" @submit="submitForm" class="px-4 my-10 max-w-3xl mx-auto space-y-3 drop-shadow-md"
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
                        type="tel" pattern="[978][0-9]{9}" name="contact" id="contact" required>
                </div>
            </div>
            <div class="form_action_button space-x-2">
                <button @click="showForm"
                    class="border border-gray-400 px-4 py-2 max-w-xs rounded bg-teal-600 text-white" type="submit"
                    value="Submit">Submit</button>
            </div>
        </form>

        <div class="grid grid-cols-4 space-y-3 space-x-3 m-10">
            <!---main card div-->
            <div v-for="(per) in timeSlots" :key="per" v-bind:index="index"
                class="max-w-sm rounded overflow-hidden border border-red-700 bg-lime-600 ml-4">

                <div class="px-6 py-4">
                    <p class="font-bold  mb-2">Start Time - {{ per.startTime }}</p>
                    <p class="font-bold  mb-2">Last Time - {{ per.endTime }}</p>
                    <div v-for="(detail, index) in users" v-bind:index="index" :key="detail">
                        <p class="font-bold mb-2">Name - {{ detail.firstName }}</p>
                        <p class="font-bold  mb-2">Mobile No - {{ detail.contact }}</p>
                        <button @click="editData(index)"
                            class="border border-yellow-400 px-4 py-1 max-w-xs rounded bg-yellow-200 text-green-600 font-bold"
                            type="submit" value="Submit">Edit</button>
                    </div>

                </div>
                <div class="px-6 pt-4 pb-2">
                    <button @click="showForm"
                        class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white ">Book Now
                    </button>
                </div>
            </div>
            <!-- </div> -->

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
            flag: false,
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
        editData(index) {
            if (confirm('Do you want to edit data?'))
                console.log("users = ", this.users[index].firstName)
            this.user.firstName = this.users[index].firstName;
            this.user.contact = this.users[index].contact;
            this.isEdit = true;
            this.editIndex = index;
        },
        showForm() {
            this.flag = true
        }
    }
}
</script>

