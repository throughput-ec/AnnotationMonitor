<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="primary">
      <b-navbar-brand style="padding-left: 20px" href="#">
        Throughput
      </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-navbar-nav>
        <b-nav-form>
          <b-input-group prepend="Database ID">
            <b-form-input placeholder="r3d100012894" v-model="dbid"></b-form-input>
            <b-button
              variant="warning"
              class="my-2 my-sm-0"
              @click="$emit('dbid')"
            >
              Search
            </b-button>
          </b-input-group>
          <div id="orcidWidget"
            data-size='lg' 
            data-clientid='APP-XXXXXXXXXXXXXXXX'
            data-env='production'
            data-scopes='/read-limited%20/activities/update%20/person/update'
            data-redirecturi='https://you-site/your-page.html' data-submituri='https://your-api-endpoint/submit'></div>
        </b-nav-form>
      </b-navbar-nav>
      </b-navbar>
  </div>
</template>

<script src="http://[YOUR SERVER LOCATION FOR THE SCRIPT]/orcid-widget.js"></script>
<script>
export default {
  name: "navbar",
  props: {
    msg: String,
    dbid: String,
  },
  data () {
    return {
    }
  },
  methods:{
    dbmodel(val) {
      this.dbid = val;
      this.dbid.push(val);
    }
  }};
</script>
