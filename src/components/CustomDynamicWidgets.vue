<template>
  <div v-if="state">
    <ais-panel v-for="attribute in state.attributesToRender" :key="attribute">
      <template #header>{{ attribute }}</template>
      <!-- You can use any other widget you want here -->
      <ais-refinement-list :attribute="attribute" searchable="true"></ais-refinement-list>
    </ais-panel>
  </div>
</template>

<script>
import { createWidgetMixin } from 'vue-instantsearch';
import { connectDynamicWidgets } from 'instantsearch.js/es/connectors';

export default {
  mixins: [
    createWidgetMixin(
      {
        connector: connectDynamicWidgets,
      },
      {
        $$widgetType: 'custom.dynamicWidgets',
      }
    ),
  ],
  computed: {
    widgetParams() {
      return {
        transformItems(items, { results }) {
          let allFacets = Object.keys(results._rawResults[0].facets);
          allFacets = allFacets.filter((el) => !items.includes(el));
          return items.concat(allFacets);
        },
        // we do not pass "widgets" to the connector, since Vue is in charge of rendering
        widgets: [],
      };
    },
  },
};
</script>
