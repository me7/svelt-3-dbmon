<script>
  export let dbs;
</script>

<style>

</style>

<table class="table table-striped latest-data">
  <tbody>

    {#each dbs as db}
      <tr>

        <td class="dbname"> {db.dbname} </td>

        <td class="query-count">
          <span class={db.lastSample.countClassName}>
             {db.lastSample.nbQueries}
          </span>
        </td>

        {#each db.lastSample.topFiveQueries as query}
          <td class="warn_long">
             {query.formatElapsed}
            <div class="popover left">
              <div class="popover-content">{query.query}</div>
              <div class="arrow" />
            </div>
          </td>
        {/each}

      </tr>
    {/each}

  </tbody>
</table>
