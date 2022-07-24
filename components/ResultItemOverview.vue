<template>
  <b-container>
    <b-card
      class="my-4"
      :img-src="result.thumbnail"
      img-alt="Image"
      :title="
        result.address.line +
        ', ' +
        result.address.city +
        ', ' +
        result.address.state_code
      "
      :sub-title="getFormattedPrice(result.price)"
    >
      <b-badge variant="dark">Beds: {{ result.beds }}</b-badge>
      <b-badge variant="dark">Baths: {{ result.baths }}</b-badge>
      <b-list-group flush>
        <h4>Key Statistics</h4>

        <b-list-group-item v-if="result.building_size">
          <small
            >{{ result.building_size.units }}:
            {{ result.building_size.size }}</small
          >
        </b-list-group-item>
        <b-list-group-item v-if="result.building_size">
          <small
            >Price/SqFt:
            {{
              getFormattedPrice(result.price / result.building_size.size)
            }}</small
          >
        </b-list-group-item>
        <b-list-group-item
          v-if="result.client_display_flags.price_change !== 0"
        >
          <small
            >Price Change:
            {{
              getFormattedPrice(result.client_display_flags.price_change)
            }}</small
          >
        </b-list-group-item>
        <b-list-group-item>
          <small>Property Type: {{ result.prop_type }}</small>
        </b-list-group-item>
        <b-list-group-item v-if="result.prop_sub_type">
          <small>Property Sub-type: {{ result.prop_sub_type }}</small>
        </b-list-group-item>
      </b-list-group>
    </b-card>
  </b-container>
</template>

<script>
export default {
    props: {
        result: {
            type: Object,
            required: true 
        },
    },
    methods: {
        getFormattedPrice(price) {
            var formatter = new Intl.NumberFormat('en-US', {
            style: 'currency',
            currency: 'USD',

            // These options are needed to round to whole numbers if that's what you want.
            //minimumFractionDigits: 0, // (this suffices for whole numbers, but will print 2500.10 as $2,500.1)
            //maximumFractionDigits: 0, // (causes 2500.99 to be printed as $2,501)
            });

            return formatter.format(price); /* $2,500.00 */
        }
    },
};
</script>

<style lang="scss" scoped>
</style>