<template>
    <div class="new-profile-form border-left-0">
        <form @submit.prevent="submitNewProfile">
            <fieldset>
                <div class="form-group">
                    <label for="exampleInputEmail1" class="form-label mt-4">Name</label>
                    <input v-model="name" type="text" class="form-control" id="exampleInputEmail1"
                        placeholder="Enter name">
                </div>
                <fieldset class="form-group">
                    <legend class="mt-4">Interests</legend>
                    <div class="form-check" v-for="interest in interests">
                        <input type="checkbox" :id="interest" :value="interest" v-model="checked_interests" />
                        <label :for="interest">{{ `${interest}` }}</label>
                    </div>
                </fieldset>
                <div class="form-group">
                    <label for="formFile" class="form-label mt-4">Profile Picture</label>
                    <input class="form-control" type="file" @change="getImageUrl" accept="image/*" id="formFile">
                </div>


                <fieldset>
                    <legend class="mt-4">Favourite?</legend>
                    <div class="form-check form-switch">
                        <input class="form-check-input" type="checkbox" v-model="favourite" id="favourite_profile">
                        <label class="form-check-label" for="favourite_profile">{{ favourite ? "Yes" : "No" }}</label>
                    </div>
                </fieldset>
                <div class="add-profile-btn">
                    <button @click="addNewProfile">Add New Profile</button>
                </div>
            </fieldset>
        </form>
    </div>
</template>

<script>
export default {
    name: 'AddNewProfile',
    data() {
        return {
            name: "",
            interests: ['Coding', 'Copy', 'Paste'],
            image_url: '',
            favourite: false,
            numberOfProfiles: 0,
            totalFavourites: 0,
            checked_interests: []
        }
    },
    methods: {
        getImageUrl(e) {
            const file = e.target.files[0]
            this.image_url = file.name;
        },
        submitNewProfile() {
            this.$emit("addNewProfile", this.name, this.image_url, this.checked_interests, this.favourite)
        }
    }
}
</script>

<style>
.new-profile-form {
    width: 300px;
    float: left;
    margin-left: 10px;
}
</style>