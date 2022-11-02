<script>
  import IoIosWifi from "svelte-icons/io/IoIosWifi.svelte";
  import IoIosBatteryFull from "svelte-icons/io/IoIosBatteryFull.svelte";
  import FaSignal from "svelte-icons/fa/FaSignal.svelte";
  let currentime;
  const interval = setInterval(function () {
    let date = new Date();
    var time = date.toLocaleString([], {
      timeStyle: "short",
      hour12: false,
    });
    currentime = time;
  }, 1);
</script>

<div class="notificationarea">
  <div class="time">{currentime}</div>
  <div class="batteryside">
    <div class="network"><FaSignal /></div>
    <div class="wifi"><IoIosWifi /></div>
    <!-- <div style="font-size: 9px; padding: 0px 3px; padding-top:1px;">LTE</div> -->
    <div class="battery"><IoIosBatteryFull /></div>
  </div>
</div>

<style>
  .notificationarea {
    font-size: 8pt;
    font-weight: bold;
    color: #ffffff;
    width: 100%;
    display: flex;
    justify-content: space-between;
    padding: 8px 10px;
  }
  .notificationarea .time {
    padding-left: 10px;
  }
  .notificationarea .batteryside {
    display: flex;
    padding-right: 20px;
  }
  .notificationarea .batteryside .network {
    color: #ffffff;
    width: 10pt;
  }
  .notificationarea .batteryside .wifi {
    color: #ffffff;
    width: 10pt;
    padding: 0px 3px;
  }
  .notificationarea .batteryside .battery {
    color: #ffffff;
    width: 10pt;
  }
</style>
