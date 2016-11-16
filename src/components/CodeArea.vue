<template>
	<div class="code-area">
		<pre class="highlighted-code" v-html="highlightedCode.value"></pre>
		<textarea v-model="localValue"></textarea>
	</div>
</template>

<script>
	import php from 'highlight.js/lib/languages/php'
	import hljs from 'highlight.js/lib/highlight'
	

	export default {
		data () {
			return {
				localValue: ''
			}
		},
		computed: {
			highlightedCode () {
				return hljs.highlightAuto(this.localValue,['php'])
			}
		},
		created () {
			hljs.registerLanguage('php',php)
			console.log(hljs.listLanguages())
		}
	}
</script>

<style type="text/css" scoped>
	.code-area {
		//background: grey;
		position: relative;
		height: 300px;
	}
	textarea {
		display: block;
		width: 100%;
		height: 300px;
		background: transparent;
		padding: 0;
		border: none;
		position: absolute;
		-webkit-text-fill-color: transparent;
	}
	textarea:focus {
		outline: none;
	}
	.highlighted-code {
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0;
		top: 0;
		margin: 0;
	}
</style>