<template>
  <section id="liverates">
    <div class="container">
      <div class="columns">
        <div class="column">
          <h2 class="title is-4">All Rates</h2>
        </div>
        <div class="column is-4">
          <b-input
            placeholder="Search..."
            type="text"
            icon="magnify"
            v-model="searchString"
            icon-clickable
            @icon-click="searchIconClick"
          >
          </b-input>
        </div>
      </div>
      <b-table
        :data="filteredData"
        :columns="columns"
        :paginated="isPaginated"
        :per-page="perPage"
        :current-page.sync="currentPage"
        :pagination-simple="isPaginationSimple"
        :pagination-position="paginationPosition"
        :default-sort-direction="defaultSortDirection"
        :pagination-rounded="isPaginationRounded"
        :sort-icon="sortIcon"
        :sort-icon-size="sortIconSize"
        default-sort="rank"
        aria-next-label="Next page"
        aria-previous-label="Previous page"
        aria-page-label="Page"
        aria-current-label="Current page"
      >
        <b-table-column
          field="rank"
          label="Rank"
          width="40"
          sortable
          numeric
          v-slot="props"
        >
          {{ props.row.rank }}
        </b-table-column>

        <b-table-column
          field="name"
          label="Name"
          sortable
          v-slot="props"
          filteredData
        >
          {{ props.row.name }}
        </b-table-column>

        <b-table-column field="symbol" label="Symbol" sortable v-slot="props">
          {{ props.row.symbol }}
        </b-table-column>

        <b-table-column field="rate" label="Rate" sortable v-slot="props">
          {{ props.row.rate }}
        </b-table-column>
      </b-table>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      searchString: "",
      cryptoData: [],
      isPaginated: true,
      isPaginationSimple: false,
      isPaginationRounded: true,
      paginationPosition: "bottom",
      defaultSortDirection: "asc",
      sortIcon: "arrow-up",
      sortIconSize: "is-small",
      currentPage: 1,
      perPage: 10,
    };
  },
  created() {
    this.getGlobalData();
  },
  methods: {
    getGlobalData() {
      fetch("https://r.easycrypto.nz/json/backenddb.json")
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          this.cryptoData = Object.entries(data).map((entry) => ({
            id: entry[0],
            ...entry[1],
          }));
          console.log(this.data);
        });
    },
  },
  computed: {
    // A computed property that holds only those data that match the searchString
    filteredData: function() {
      var search_array = this.cryptoData,
        searchString = this.searchString;

      if (!searchString) {
        return search_array;
      }

      searchString = searchString.trim().toLowerCase();

      search_array = search_array.filter((item) => {
        if (
          item.name.toLowerCase().indexOf(searchString) !== -1 ||
          item.symbol.toLowerCase().indexOf(searchString) !== -1
        ) {
          return item;
        }
      });

      // Return an array with the filtered data.
      return search_array;
    },
  },
};
</script>

<style lang="scss">
#liverates {
  position: relative;
  padding: 80px 0;
  .pagination-link.is-current {
    background-color: $primary-color;
  }
  .table {
    background-color: $bg-color;
    border-radius: 5px;
    box-shadow: 0 17px 30px 6px rgb(0 0 0 / 5%);
    th,
    td {
      padding: 15px 20px;
      border-width: 0 0 1px;
    }
    th {
      font-weight: 800;
    }
    td {
      border-bottom: 1px solid $bg-light;
    }
    tr {
      &:last-child {
        td {
          border-bottom: 0;
        }
      }
    }
  }
}
</style>
