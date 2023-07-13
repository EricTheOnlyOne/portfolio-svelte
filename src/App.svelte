<main>
	<!-- Github & LinkedIn -->
        <div class="credits">
            <div class="github">
                <a href="https://github.com/abdulsohailmohd/sorting-visualizer" target="_blank" title="Github">
                    <img src="assets/github-logo.svg" alt="Github" />
                </a>
            </div>
            <div class="linkedin">
                <a href="https://www.linkedin.com/in/sohail-js" target="_blank" title="LinkedIn">
                    <img src="assets/linkedin.svg" alt="LinkedIn" />
                </a>
            </div>
        </div>

        <div class="page-wrapper">
            <div class="toolbar toolbar-top">
                <button id="generateArrayBtn" class="btn btn-primary-outline">Generate Array</button>

                <!-- Array Size -->
                <div class="slider-container">
                    <label for="arraySizeSliderElement">Array size</label>
                    <input type="range" min="4" max="200" value="150" class="slider" id="arraySizeSliderElement">
                </div>

                <!-- Animation SPeed -->
                <div class="slider-container animation-speed">
                    <label for="animationSpeedSliderElement">Animation Speed</label>
                    <div>
                        <span>Fast</span>
                        <input type="range" min="1" max="500" value="1" class="slider" id="animationSpeedSliderElement">
                        <span>Slow</span>
                    </div>
                </div>

                <!-- Sorting Algorithm -->
                <select name="sorting-algorithms" id="sortingAlgorithms">
                    <option value="mergeSort" selected>Merge Sort</option>
                    <option value="quickSort">Quick Sort</option>
                </select>
            </div>

            <div id="barsElement"></div>

            <div class="bottom">
                <div class="slider-container">
                    <input type="range" min="0" max="100" value="0" class="slider" id="sliderElement">
                </div>

                <div class="toolbar toolbar-bottom">
                    <button id="toggleAnimationBtn" class="btn btn-primary btn-rounded" title="Play / Pause">
                        <i class="mdi mdi-play"></i>
                    </button>
                    <button id="stopAnimationBtn" class="btn btn-rounded btn-secondary" title="Stop">
                        <i class="mdi mdi-stop"></i>
                    </button>
                    <!-- <button onclick="pauseAnimation()">Pause</button> -->
                </div>
            </div>
        </div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}


	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	* {
      font-family: "Jura", sans-serif; }

    body {
      background-color: #28293d;
      color: #fff; }

    .page-wrapper {
      display: flex;
      flex-direction: column;
      flex-wrap: wrap;
      height: calc(100vh - 16px);
      margin: 0;
      padding: 0 50px; }

    #barsElement {
      display: flex;
      justify-content: center;
      flex-grow: 1;
      padding-top: 20px;
      width: 100%; }

    .bar {
      /* border: 2px solid black; */
      background: #9dbff8;
      width: 20px;
      margin-right: 1px;
      position: relative;
      border-radius: 18px; }

    .un-ordered {
      background: red; }

    .sorted {
      background: #05c270; }

    .ordered {
      background: #05c270; }

    input.slider {
      width: 100%; }

    .start:before {
      content: "\F061F";
      position: absolute;
      top: -24px;
      left: -2px;
      color: #fff;
      display: inline-block;
      font: normal normal normal 24px/1 "Material Design Icons";
      font-size: inherit;
      text-rendering: auto;
      line-height: inherit;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      font-size: x-large; }

    .end:before {
      content: "\F0620";
      position: absolute;
      top: -24px;
      right: -2px;
      color: #fff;
      display: inline-block;
      font: normal normal normal 24px/1 "Material Design Icons";
      font-size: inherit;
      text-rendering: auto;
      line-height: inherit;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      font-size: x-large; }

    .comparing {
      display: flex;
      justify-content: center; }
      .comparing::after {
        content: "\F005D";
        position: absolute;
        bottom: -23px;
        z-index: 10;
        color: #93ff5b;
        display: inline-block;
        font: normal normal normal 24px/1 "Material Design Icons";
        font-size: inherit;
        text-rendering: auto;
        line-height: inherit;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        font-size: x-large; }

    /* .mid {
        border-top: 20px solid pink;
        margin-top: -20px;
      } */
    .toolbar {
      display: flex;
      justify-content: center;
      padding: 15px 0;
      align-items: center; }

    .toolbar-top > * {
      margin-right: 30px; }

    .toolbar-bottom > button:first-child {
      margin-right: 7px; }

    /* .bottom {
      } */
    .animation-speed > div {
      display: flex;
      align-items: center;
      margin-top: 5px; }
      .animation-speed > div > *:not(:first-child) {
        margin-left: 10px; }

    .pivot {
      /* border: 2px solid red; */
      background: #ffac00; }

    .swap {
      background-color: #f13737; }

    .btn {
      padding: 10px;
      border: none;
      border-radius: 10px;
      cursor: pointer; }
      .btn-primary {
        background-color: #3568d4;
        color: #fff;
        box-shadow: 0px 5px 13px 0px #1f58d18c; }
      .btn-primary-outline {
        border: 1px solid #3568d4;
        color: #fff;
        box-shadow: 0px 5px 13px 0px #1f58d18c;
        background-color: transparent; }
      .btn-secondary {
        background-color: #28c328;
        color: #fff;
        box-shadow: 0px 5px 13px 0px #1fd13d8c; }
      .btn-rounded {
        border-radius: 100px; }

    select {
      padding: 9px 5px;
      border-radius: 10px;
      border: 1px solid #3568d4;
      color: #fff;
      box-shadow: 0px 5px 13px 0px #1f58d18c;
      background-color: transparent;
      cursor: pointer; }
      select option {
        color: #000; }

    /* The slider itself */
    .slider {
      -webkit-appearance: none;
      /* Override default CSS styles */
      appearance: none;
      width: 100%;
      /* Full-width */
      height: 5px;
      /* Specified height */
      background: #d3d3d3b7;
      /* Grey background */
      outline: none;
      /* Remove outline */
      -webkit-transition: 0.2s;
      /* 0.2 seconds transition on hover */
      transition: background 0.2s;
      cursor: pointer;
      /* Mouse-over effects */
      /* The slider handle (use -webkit- (Chrome, Opera, Safari, Edge) and -moz- (Firefox) to override default look) */ }
      .slider:hover {
        background: #d3d3d3; }
      .slider::-webkit-slider-thumb {
        -webkit-appearance: none;
        /* Override default look */
        appearance: none;
        width: 15px;
        /* Set a specific slider handle width */
        height: 15px;
        /* Slider handle height */
        background: #3568d4;
        /* Green background */
        cursor: pointer;
        /* Cursor on hover */
        border-radius: 50px;
        box-shadow: 0px 5px 13px 0px #1f58d18c; }
      .slider::-moz-range-thumb {
        width: 15px;
        /* Set a specific slider handle width */
        height: 15px;
        /* Slider handle height */
        background: #3568d4;
        /* Green background */
        cursor: pointer;
        /* Cursor on hover */
        border-radius: 50px;
        box-shadow: 0px 5px 13px 0px #1f58d18c; }

    .credits {
      position: fixed;
      right: 0;
      top: 50%;
      transform: translateY(-50%);
      background-color: #fff;
      box-shadow: 0 0 8px 3px #0a0a0a5c;
      padding: 5px;
      border-top-left-radius: 10px;
      border-bottom-left-radius: 10px; }
      .credits > div {
        transition: all .1s; }
        .credits > div img {
          width: 20px;
          height: 20px; }
        .credits > div:not(:first-child) {
          margin-top: 5px; }
        .credits > div:hover {
          transform: scale(1.1); }

    @supports (-ms-ime-align: auto) {
      .slider-container {
        width: 200px; }
      .bottom .slider-container {
        width: 800px;
        margin: 0 auto; }
      .slider {
        background-color: #fff; } }
</style>