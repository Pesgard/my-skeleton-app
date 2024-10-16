<script>
	import '../app.css';
	import Appbar from '$lib/Components/Navigation/Appbar.svelte';
	import MobileMenu from '$lib/Components/Navigation/MobileMenu.svelte';
	import DesktopMenu from '$lib/Components/Navigation/DesktopMenu.svelte';

	let mobileScreen = $state(false);

	// Cleanup event listener on component destroy
	$effect(() => {
		window.onresize = () => {
			let context = window.innerWidth;

			if (context < 640) {
				mobileScreen = true;
			} else {
				mobileScreen = false;
			}
		};
	});
</script>

<Appbar />
{#if mobileScreen}
	<MobileMenu />
{:else}
	<DesktopMenu />
{/if}
