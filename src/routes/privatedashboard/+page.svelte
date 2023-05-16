<script>
	import { authStore } from '../../store/authStore';

	let email;
	authStore.subscribe((curr) => {
		email = curr?.currentUser?.email;
	});
</script>

{#if $authStore.currentUser}
	<div
		class="container-fluid mx-auto min-h-screen flex flex-col justify-center items-center text-center mt-2 bg-cover bg-no-repeat"
		style="background-image: url('/hero1.jpg');"
	>
		<div class="w-5/6 bg-slate-200 p-8 rounded-md">
			<div>
				<h1 class="text-xl font-semibold pb-2">Email registrado correctamente</h1>
				<span>- {email}</span>
			</div>
			<div class="pt-10">
				<p>
					Gracias por registarte, recibiras informacion todos los meses a tu email sobre rutinas y
					planes Premium que ofrece HealtyWay
				</p>
			</div>
		</div>
	</div>
{:else}
	<div
		class="container-fluid mx-auto min-h-screen flex flex-col justify-center items-center text-center mt-2 bg-cover bg-no-repeat"
		style="background-image: url('/hero1.jpg');"
	>
		<span class="w-5/6 bg-slate-200 p-8 rounded-md">Loading...</span>
	</div>
{/if}
