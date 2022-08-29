<template>
  <div>
    {{ this.dbid }}
    <navbar @clicked="getdb"> </navbar>
    <b-container>
      <b-row>
        <annotationlist dbid="r3d100012894" />
      </b-row>
    </b-container>
  </div>
</template>

<script>
import navbar from "./navbar/navMain.vue";
import annotationlist from "./annotationtables/annotationlist.vue";

export default {
  name: "HelloWorld",
  components: {
    navbar,
    annotationlist,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      dbid: null,
  }},
  methods: {
    getdb(val) {
      this.dbid = val;
    },
  },
};
</script>
