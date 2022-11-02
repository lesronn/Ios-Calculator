<script>
  import NotificationArea from "./components/NotificationArea.svelte";

  let answer = 0;
  let input = 0;
  let state = null;

  function Operator() {
    switch (state) {
      case "add":
        answer += parseFloat(input);
        input = "";
        break;
      case "substract":
        answer -= parseFloat(input);
        input = "";
        break;
      case "multiply":
        answer *= parseFloat(input);
        input = "";
        break;
      case "divide":
        answer /= parseFloat(input);
        input = "";
        break;
      default:
        answer = parseFloat(input);
        input = "";
        break;
    }
  }
  function setOperation(operation) {
    Operator();
    state = operation;
  }
  function setValue(value) {
    if (input.toString() == "0" || state == "equal") {
      input = "";
    }
    if (state == "equal") {
      state = null;
    }
    if (value == "C") {
      answer = 0;
      state = null;
      input = 0;
      return;
    }

    input = input + value;
  }
  function equal() {
    Operator();
    input = answer.toLocaleString("en-US");
    state = "equal";
  }
</script>

<main>
  <div class="iphone">
    <div class="screen">
      <NotificationArea />
      <div class="screen_container">
        <input
          type="text"
          class="display_panel"
          bind:value={input}
          readonly="true"
        />
        <!-- <div class="display_panel"><span>92</span></div> -->
        <div class="calcbtndiv">
          <div class="calcbtns">
            <div
              on:click={() => {
                setValue("C");
              }}
              class="clear row1 calcbtn"
            >
              AC
            </div>
            <div class="calcbtn row1">+/-</div>
            <div class="calcbtn row1">%</div>
            <div
              on:click={() => {
                setOperation("divide");
              }}
              class="sign calcbtn"
            >
              &divide;
            </div>
            <div
              on:click={() => {
                setValue(7);
              }}
              class="num calcbtn"
            >
              7
            </div>
            <div
              on:click={() => {
                setValue(8);
              }}
              class="num calcbtn"
            >
              8
            </div>
            <div
              on:click={() => {
                setValue(9);
              }}
              class="num calcbtn"
            >
              9
            </div>
            <div
              on:click={() => {
                setOperation("multiply");
              }}
              class="sign calcbtn"
            >
              &times;
            </div>
            <div
              on:click={() => {
                setValue(4);
              }}
              class="num calcbtn"
            >
              4
            </div>
            <div
              on:click={() => {
                setValue(5);
              }}
              class="num calcbtn"
            >
              5
            </div>
            <div
              on:click={() => {
                setValue(6);
              }}
              class="num calcbtn"
            >
              6
            </div>
            <div
              on:click={() => {
                setOperation("substract");
              }}
              class="sign calcbtn"
            >
              -
            </div>
            <div
              on:click={() => {
                setValue(1);
              }}
              class="num calcbtn"
            >
              1
            </div>
            <div
              on:click={() => {
                setValue(2);
              }}
              class="num calcbtn"
            >
              2
            </div>
            <div
              on:click={() => {
                setValue(3);
              }}
              class="num calcbtn"
            >
              3
            </div>
            <div
              on:click={() => {
                setOperation("add");
              }}
              class="sign calcbtn"
            >
              +
            </div>
            <div
              on:click={() => {
                setValue(0);
              }}
              class="num double calcbtn"
            >
              0
            </div>
            <!-- <div class="num calcbtn">0</div> -->
            <div
              on:click={() => {
                setValue(".");
              }}
              class="num calcbtn"
            >
              .
            </div>
            <div on:click={equal} class="sign calcbtn">=</div>
          </div>
        </div>
        <div class="swipe_container"><div class="homeswipe" /></div>
      </div>
    </div>

    <div class="notch">
      <div class="mouthpiece" />
      <div class="camera">
        <div class="camera1" />
      </div>
    </div>

    <div class="silentswicth" />
    <div class="volume">
      <div class="volup" />
      <div class="voldown" />
    </div>
    <div class="powerbtn" />
  </div>
</main>

<style>
  .screen_container {
    padding: 0 10px;
    color: white;
    height: calc(100% - 40px) !important;
    display: flex;
    flex-direction: column;
  }
  .screen_container .display_panel {
    display: flex;
    flex: 20%;

    text-align: right;

    margin-top: 40px;
    font-size: 55px;
    font-family: "sflight";
    outline: none !important;
    border: none !important;
    cursor: grab;
    background: #000000;
    color: #ffffff !important;
    overflow: hidden !important;
  }

  .screen_container .calcbtndiv {
    display: flex;
    flex: 80%;
    /* border: 2px solid red; */
    margin-bottom: 20px;
  }
  .calcbtndiv .calcbtns {
    display: grid;
    width: 100%;
    grid-template-columns: auto auto auto auto;
    justify-content: space-between;
    margin-top: 15px;
    padding-bottom: 10px;
  }
  .calcbtns .calcbtn {
    padding: 10px;
    height: 30px;
    width: 30px;
    cursor: pointer;
    font-size: 25px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    outline: none !important;
  }
  .sign {
    background: #ff9500;
  }
  .num {
    background: #333;
  }
  .row1 {
    background: #a5a5a5;
    color: black;
  }
  .double {
    grid-column: 1 / span 2;
    width: 85px !important;
    border-radius: 25px !important;
    justify-content: start !important;
    text-indent: 8px;
  }
  .swipe_container {
    width: 100%;
    display: flex;
    justify-content: center;
  }
  .homeswipe {
    width: 80px;
    height: 3px;
    background: white;
    border-radius: 10px;
    transform: translateY(-10px);
  }
</style>
