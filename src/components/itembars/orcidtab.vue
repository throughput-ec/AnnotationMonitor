<template>
  <div align="left">
    <b-button href="https://orcid.org" target="_blank" pill sm>
      ORCID: <b-badge>{{ orcid }}</b-badge>
    </b-button>
  </div>
</template>
<script>
export default {
  name: "orcidbadge",
  props: ["orcid"],
};
</script>
