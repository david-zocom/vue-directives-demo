<template>
	<div id="app">
		<div v-bind:class="cssTheme">
			<h1>Rubrik</h1>
			<p>Lite text</p>
			<button @click="switchThemeGreen">Byt till grönt tema</button> <br />
			<button @click="switchThemeOther">Byt till annat tema</button>
		</div>
		<hr />

		<div>
			<label><input type="checkbox" @change="changeButtonState" /> Gör klickbar</label> <br />
			<label><input type="checkbox" v-model="buttonIsEnabled" /> Gör klickbar</label> <br />
			<button v-bind:disabled="!buttonIsEnabled"> Klickbar? </button>
			<span v-if="buttonIsEnabled">Synlig!</span> <br />
		</div>

		<hr />

		<div>
			<label><input type="radio" value="2" name="numbers" @change="changeRadio" /> Två </label>
			<label><input type="radio" value="3" name="numbers" @change="changeRadio" /> Tre </label>
			<ul>
				<li v-for="n in numbers" v-if="n % numbersT === 0">
					{{ n }}
				</li>
			</ul>
		</div>

    Tomte! {{ color }}
	<div v-if="viewOption1"> option 1 </div>
	<div v-if="!viewOption1"> option 2 </div>
	<ul>
		<li v-for="x in [2, 4, 8, 16]">
			<strong>{{ x }}</strong>!!!!
		</li>
	</ul>
	Please enter your favourite animal:
	<input type="text" v-model="favAnimal" placeholder="Animal" />
	<br /> {{ favAnimal }}
	<br />The animal has {{ animalLength }} letters.
  </div>
</template>

<script>
  export default {
    name: 'app',
	data: function() {
		return {
			numbers: [10, 11, 12, 2, 13, 1, 14000, 35, 79, -12],
			numbersT: 2,
			buttonIsEnabled: false,
			//buttonIsDisabled: true,
			cssTheme: 'themeBlue',
			favAnimal: 'kanin',
			viewOption1: false,
			color: 'magic',
			another: true,
			user: {
				name: '',
				email: ''
			}
		};
	},  // data
	computed: {
		animalLength: function() {
			return this.favAnimal.length;
		}
	},  // computed
	methods: {
		switchThemeGreen: function(event) {
			this.cssTheme = 'themeBlue';
		},
		switchThemeOther: function(event) {
			this.cssTheme = 'themeGreen';
		},
		changeButtonState: function(event) {
			this.buttonIsEnabled = event.target.checked;
		},
		changeRadio: function(event) {
			console.log('changeRadio', event.target.value);
			this.numbersT = event.target.value;
		}
	}
  }
</script>

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>

<!-- Global CSS -->
<style>
.themeBlue {
	background-color: #BCF5A9;
}
.themeGreen {
	background-color: #E2A9F3;
}
  code {
    font-family: Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif;
    font-size: 0.9em;
    white-space: pre-wrap;
    color: #2c3e50;
  }

  code::before, code::after {
    content: '`';
  }
</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
  #app {
    font-family: sans-serif;
  }

  #app h1,li {
    color: #2c3e50;
    font-weight: 300;
    margin: 20px;
  }

  .banner {
    height: 200px;
    background-color: #f6f6f6;
    padding: 50px 10px;
  }

  .bottom {
    padding: 80px 10px;
    font-size: 24px;
    font-weight: 300;
  }

  .fade {
    font-size: 14px;
  }

  .logo {
    animation: spin 4s 1s infinite linear
  }

  @keyframes spin {
    from {transform:rotate(0deg);}
    to {transform:rotate(360deg);}
  }
</style>
