<script>
	import Nav from '../components/layout/Nav.svelte';
	import Navbar from '../components/layout/mpm/Navbar.svelte';
	import { nav,subNav } from '../store';

	import { stores, goto } from '@sapper/app';
	const { session } = stores();
	import { onMount } from 'svelte';
	
	onMount( () => {
		if(window && window.localStorage){
			$session.user = JSON.parse(localStorage.getItem('user'));
			if(!$session.user){
				goto('/login');
			}
			$session.lan = localStorage.getItem('lan');
		}
	})
	$: marginLeft = $nav.showSideBar ? '250px' : '0px' ;
	
	export let segment;
</script>

<style>
</style>

{#if $session.user}
<Nav {segment}/>
{/if}

<div id="content" style="margin-left:{marginLeft};" class="mt-mpm-6" >
	{#if $session.user}
		<Navbar></Navbar>
	{/if}
	<slot>zzz</slot>
</div>
