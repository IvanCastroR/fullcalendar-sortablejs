<script lang="ts">
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
</script>

<Header />



<main>
	<nav class="navbar navbar-expand-lg  navbar-dark bg-dark">
		<div class="collapse navbar-collapse" id="navbarNav">
			<ul class="navbar-nav">
			<li class="nav-item">
				<a class="nav-link" href="/draggable">Draggable</a>
			</li>
			<li class="nav-item">
				<a class="nav-link" href="/thirdPartyDraggable">ThirdPartyDraggable</a>
			</li>
			</ul>
		</div>
	</nav>
	<slot />
</main>




