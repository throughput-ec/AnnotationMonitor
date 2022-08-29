<template>
  <div style="padding-top: 10px;border-width:2px;border-style:solid">
    <b-modal id="modal-1" title="Flag Annotation">
      Flag this annotation?
    </b-modal>
    <b-modal id="modal-2" title="Flag Annotation">
      Mark annotation as resolved?
    </b-modal>
    <b-modal id="modal-3" title="Reply to Annotation">
      Add an annotation to this note.
      <b-form-textarea v-model="message" placeholder="add multiple lines" >
      </b-form-textarea>
    </b-modal>
    <b-container>
      <b-row>
        <div style="padding: 5px">
          <orcidtab :orcid="itemData[0].orcid"></orcidtab>
        </div>
      </b-row>
      <b-row>
        <div style="padding: 10px; border-style: ridge; border-width: 1px">
          {{ itemData[0].annotation }}
        </div>
      </b-row>
      <b-row>
        <div align="right" style="padding: 10px">
          <b-button variant="danger" v-b-modal.modal-1>Flag</b-button>
          <b-button variant="success" v-b-modal.modal-2>Resolve</b-button>
          <b-button variant="primary" v-b-modal.modal-3>Reply</b-button>
        </div>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import orcidtab from "../itembars/orcidtab.vue";
// import flagmodal from '../modals/flaggingModal.vue';

export default {
  components: {
    orcidtab,
  },
  name: "annotationlist",
  props: ["itemData"],
  methods: {
    runFlag() {
      this.flagger = true;
    },
  },
  data() {
    return {
      flagger: false,
    }}};
</script>
