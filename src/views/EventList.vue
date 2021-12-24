<template>
  <div class="event">
    <h1>Events</h1>
    <Eventcard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import Eventcard from "../components/Eventcard.vue";
import axios from "axios";
export default {
  name: "Home",
  components: {
    Eventcard,
  },
  data() {
    return {
      events: null,
    };
  },
  created() {
    axios
      .get("http://my-json-server.typicode.com/uthsobcb/eventy-vue/events")
      .then((res) => {
        console.log(res.data);
        this.events = res.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped></style>
