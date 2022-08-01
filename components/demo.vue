<template>
    <div class="mt-5">
        <form @submit="submitForm" class="px-4 my-10 max-w-3xl mx-auto space-y-3 drop-shadow-md" method="post">
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
                <div class="w-1/3 mb-4 bg-red-400">
                    <p>Name - {{ per.firstName }}</p>
                    <p>Mobile No - {{ per.contact }}</p>
                    <button @click="editData(index)" class="border border-gray-400 px-3 py-1 max-w-xs rounded bg-red-600 text-white"
                        type="submit" value="Submit"> Edit Details</button>
                </div>
            </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
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
            console.log("users = ", this.users[index].firstName)
            this.user.firstName = this.users[index].firstName;
            this.user.contact = this.users[index].contact;
            this.isEdit = true;
            this.editIndex = index;
        },
    }
}
</script>


<style>
table,
tr,
td {
    border: 1px black solid;
}
</style>