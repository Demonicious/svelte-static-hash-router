### Svelte Static Hash Router
A Simple & Easy to use Static page router for Svelte.
#### 1. Installation
It's available on NPM under the name 'svelte-static-hash-router'.
You can Install the package with the command below:

`npm i -D svelte-static-hash-router`

#### 2. Usage Example
```js
<script>
	import Router from "svelte-static-hash-router/Router.svelte";
	import Link from "svelte-static-hash-router/Link.svelte";

	import Index from "./Components/Index.svelte";
	import About from "./Components/About.svelte";
	import ErrorComponent from "./Components/ErrorComponent.svelte";
</script>

<main>
	<div class="nav">
		<ul>
			<li>
				<Link to="/">Home Page</Link>
			</li>
			<li>
				<Link attributes={{ class="nav-link", target="_blank" }} to="/about">About Me</Link>
			</li>
		</ul>
	</div>
	
	<Router 
		routes={[
			{
				path: '/',
				component: Index,
				props: {
					some_property: "property_value"
				}
			},
			{
				path:  '/about',
				component: About
			}
		]} 
		
		notfound={ErrorComponent}  
	/>
</main>
```
The "Router" component needs to have a "routes" prop that is an array of Routes.

Each "Route" has a Path & and a Component. Optionally, You may pass "props" to the component which can be accessed with an "export let property_name" statement inside the Component.

The "Link" component needs to have a "to" prop that determines where the Link will go to.
You may specify any attributes for the Anchor tag by passing in a "attributes" prop as shown above.

#### 3.  Notes
Currently this router can only be used for Static Routes. But I plan on making a Router for dynamic routes very soon.
