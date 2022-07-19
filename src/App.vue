<template>
  {{ add_profile_check }}
  <div class="main">
    <NewProfileForm @addNewProfile="addNewProfile" />
    <div class="main__profile-cards">

      <div>
        <UserProfile v-bind:name="profile.name" v-bind:profession="profile.checked_interests"
          v-bind:image_url="profile.image_url" v-bind:favourite="profile.favourite" @favorite="updateTotalFavorites"
           />
      </div>
    </div>
  </div>
</template>

<script>

import NewProfileForm from './components/NewProfileForm.vue'
import UserProfile from './components/UserProfile.vue';

export default {
  name: "Twotter",
  components: { UserProfile, NewProfileForm },

  data() {
    return {
      numberOfProfiles: 0,
      add_profile_check: false,
      totalFavourites: 0,
      profile: {
        name: "",
        image_url: '',
        favourite: false,
        checked_interests: []
      }
    }
  },

  mounted() {
    this.numberOfProfiles = 0;
  },

  methods: {
    addNewProfile(name, image_url, checked_interests, favourite) {
      this.profile.name = name;
      this.profile.image_url = image_url;
      this.profile.checked_interests = checked_interests;
      this.profile.favourite = favourite;
      this.numberOfProfiles++;
    },
    updateTotalFavorites(isFavourite) {
      isFavourite ? this.totalFavourites++ : this.totalFavourites--
    },
  }
}
</script>


<style>
.main__profile-cards {
  display: flex;
  justify-content: space-evenly;
  float: right;
}

.add-profile-btn {
  text-align: center;
}

.main__count-followers {
  display: block;
  text-align: center;
}
</style>