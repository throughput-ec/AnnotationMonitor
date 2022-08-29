<template>
  <div>
    <b-container>
      <b-row>
        <h2>List of Annotations for {{ this.dbid }}</h2>
        <div v-if="this.loading">
          <b-spinner type="grow"></b-spinner>
        </div>
        <div v-else style="border-width: 2px; border-style: ridge;">
          <b-table
            ref="annotTable"
            striped
            sticky-header
            hover
            selectable
            select-mode="single"
            :items="this.annotationlist"
            :fields="this.fields"
            @row-selected="onRowSelected"
          ></b-table>
        </div>
      </b-row>
      <b-row>
        <div style="padding: 10px; border-style: ridge; border-width: 1px">
          <focustab :itemData="this.selected"></focustab>
        </div>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import focustab from "./focusPanel.vue";

export default {
  name: "annotationlist",
  props: ["dbid"],
  components: {
    focustab,
  },
  data() {
    return {
      database: null,
      fields: [{
          key: "annotationauthor",
          sortable: true,
        },
        {
          key: "orcid",
          sortable: true,
        },
        {
          key: "annotation",
          sortable: true,
        },
        {
          key: "date",
          sortable: true,
        },
      ],
      loading: true,
      annotationlist: [],
      selected: {},
    };
  },
  mounted() {
    this.pullAPI();
  },
  kwText: {
      handler(val) {
        this.dbid = this.allKeywords.filter(function (kw) {
          return kw.term.includes(val.toLowerCase());
        });
      },
    },
  methods: {
    onRowSelected(items) {
      this.selected = items;
    },
    pullAPI() {
      fetch("https://throughputdb.com/api/ccdrs/annotations?dbid=r3d100012894")
        .then(function (response) {
          return response.json();
        })
        .then((data) => {
          this.annotationlist = data.data;
          this.loading = false;
        });
    },
  },
};
</script>
