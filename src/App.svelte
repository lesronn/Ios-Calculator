<script>
  import Phone from "./Phone.svelte";
</script>

<main>
  <div class="left"><Phone /></div>
  <div class="right">
    <div class="container">
      <div class="top" />

      <div class="bottom">
        <p>
          Developed with ❤️ | by <a
            href="https://github.com/lesronn"
            target="_blank"><strong>Lesron</strong></a
          >.
        </p>
      </div>
    </div>
  </div>
</main>
<div class="responsive">
  <h3>This App is not Available for mobile screens</h3>
</div>

<style>
  main {
    width: 100%;
    height: 100vh !important;
    display: flex;
    flex-direction: row;
  }
  .responsive {
    text-align: center;
    display: none;
  }
  main .left {
    height: 100vh !important;
    width: 100%;
    background: #333;
    display: flex;
    justify-content: center !important;
    align-items: center !important;
  }

  main .right {
    height: 100%;
    width: 100%;
    background: #ff9500;
    font-family: "Rubik" !important;
  }
  .right .container {
    display: flex;
    height: 100vh;
    width: 100%;
    flex-direction: column;
  }
  .container .top {
    display: flex;
    flex: 95%;
    height: 100%;
    width: 100%;
    padding: 50px;
  }
  .top h2 span {
    color: white;
    background: crimson;
    padding: 5px;
    border-radius: 7px;
  }
  .container .bottom {
    display: flex;
    height: 100%;
    font-size: 16px;
    flex: 5%;
    height: 100%;
    border-top: 1px dashed #333;
    color: black;
    align-items: center;
    justify-content: center;
  }
  .bottom a {
    color: #333;
  }

  @media (max-width: 600px) {
    main {
      display: none;
    }
    .responsive {
      display: block;
    }
  }
</style>
