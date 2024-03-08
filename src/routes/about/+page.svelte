<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head>

<script>
	/**
	 * @description following this:
	 * @see https://frontendmasters.com/courses/svelte-v2/svelte-basics/
	 * @desc but do not be fooled by this
	 * @see https://learn.svelte.dev/tutorial/html-tags
	 * @desc -- you can not nest script tags in divs
	 */
	import Nested from './../../components/NestedText.svelte'
	let name = 'Svelte';
	let dancer = 'rick Astley'
	let src = 'https://www.icegif.com/wp-content/uploads/2023/01/icegif-155.gif';
	let string = 'this is some <strong>HTML</strong>, but it is not sanitized!'

	let count = 0
	function increment (){
		// event handler here
		count++
	}

	// reactive declaration
	$: doubled = count * 2;
	// whenever something inside the reactive declaration changes, the code is excecuted
	$: {
		console.log('count is: ',count)
		console.log('this is also logged when count changes')
	}

	// using array methods will not cause an update, cause svelte is looking for indexes, nums
	let numbers = [1,2,3,4]

	function addNum(){
		numbers.push(numbers.length + 1)
	}

	$: sum = numbers.reduce((t,n)=> t+n,0)





</script>
<style>
	p { 
		color: goldenrod;
		font-family: 'Comic Sans MS', cursive;
	}
</style>

<div class="text-column">
	<h1>About this app</h1>

	<p>
		This is a <a href="https://kit.svelte.dev">SvelteKit</a> app. You can make your own by typing the
		following into your command line and following the prompts:
	</p>

	<pre>npm create svelte@latest</pre>

	<p>
		The page you're looking at is purely static HTML, with no client-side interactivity needed.
		Because of that, we don't need to load any JavaScript. Try viewing the page's source, or opening
		the devtools network panel and reloading.
	</p>

	<p>
		The <a href="/sverdle">Sverdle</a> page illustrates SvelteKit's data loading and form handling. Try
		using it with JavaScript disabled!
	</p>
</div>

<div class="tutorial-container">
	<h2> using this setup to run through the totorial </h2>
	
	<div class="separator"></div>
	<div class="tutorial-wrapper">
		<h4>Hello {name.toUpperCase()}!</h4>
	</div>

	<div class="separator"></div>
	<div class="tutorial-wrapper">
		<img src={src} alt="{dancer} rickrolls"/>
	</div>

	<div class="separator"></div>
	<div class="tutorial-wrapper">
		<p> A paragraph. It inherits styles from the files style tag!</p>
		<Nested />
	</div>

	<div class="separator"></div>
	<div class="tutorial-wrapper">
		<p>{@html string}</p>
	</div>

	<div class="separator"></div>
	<div class="tutorial-wrapper">
		<button on:click={increment}>
			clicked {count}
			{count === 1 ? 'time' : 'times'}
		</button>
		<p>{doubled}</p>
	</div>

	<div class="separator"></div>
	<div class="tutorial-wrapper">
		<h4> { numbers.join(' + ') } = {sum} </h4>
		<button on:click={addNum}>
			Add a number
		</button>
	</div>

	<div class="separator"></div>

</div>
