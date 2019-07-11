<script>
  import Table from "./Table.svelte";
  import * as perfMonitor from "perf-monitor";
  import env from "./ENV";

  perfMonitor.startFPSMonitor();
  perfMonitor.startMemMonitor();
  perfMonitor.initProfiler("view update");

  let data = env.generateData().toArray();

  function redraw() {
    perfMonitor.startProfile("view update");
    data = env.generateData().toArray();
    perfMonitor.endProfile("view update");
    setTimeout(redraw, env.timeout);
  }
  redraw();
</script>

DBmon
<Table dbs={data} />
