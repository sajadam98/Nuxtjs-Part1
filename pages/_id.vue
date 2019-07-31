<template>
  <div id="page">
    <b-card
      :img-src="`https://api.adorable.io/avatars/285/${user.email}.png`"
      img-alt="Image"
      img-top
      title="User Information"
      tag="article"
      class="mb-2"
    >
      <b-card-text>
        <div id="info-card">
          <a id="titles">
            <b>Name :</b>
          </a>
          <a id="values">
            <b>
              {{ user.name }}
              <br />
            </b>
          </a>
          <a id="titles">
            <b>Email :</b>
          </a>
          <a id="values">
            <b>
              {{ user.email }}
              <br />
            </b>
          </a>
          <a id="titles">
            <b>Status :</b>
          </a>
          <a id="values">
            <b>
              {{ user.status }}
              <br />
            </b>
          </a>
        </div>
      </b-card-text>
      <nuxt-link to="/users">
        <b-button variant="primary" id="btn-back">Back</b-button>
      </nuxt-link>
    </b-card>
  </div>
</template>
<script>
import axios from "axios";
import { mapState } from "vuex";
// import router from '../router'
var _ = require("lodash");

export default {
  data() {
    return {
    }
  },
  computed: {
    ...mapState(["users"])
  },
  asyncData({ store, params }) {
    return axios
      .get("https://sajadamiri-demo.herokuapp.com/api/users/" + params.id)
      .then(res => ({
        user: res.data[0]
      }));
  },
  methods: {
    navigate() {
      //   router.push({ name: 'users' })
    }
  }
};
</script>
<style scoped>
.mb-2 {
  margin-top: 15%;
  margin-right: 35%;
  margin-left: 35%;
  width: 30%;
}
#titles {
  font-size: 20px;
  margin-top: 20px;
}
#values {
  color: blue;
  font-size: 19px;
  margin-top: 20px;
}
#btn-back {
  margin-top: 25px;
}
#info-card {
  margin-top: 20px;
}
#page {
  text-align: center;
}
</style>
