<script>
	import { onMount } from 'svelte';
	import '../app.css';
	import Footer from '../lib/components/Footer.svelte';
	import Navbar from '../lib/components/Navbar.svelte';
	import { auth } from '../lib/firebase/firebase.client';
	import { authStore } from '../store/authStore';

	onMount(() => {
		const unsubscribe = auth.onAuthStateChanged((user) => {
			authStore.update((current) => {
				return { ...current, isLoading: false, currentUser: user };
			});
		});
	});
</script>

<Navbar />
<slot />
<Footer />
