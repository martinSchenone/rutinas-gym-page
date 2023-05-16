<script>
	import { authHandlers, authStore } from "../../store/authStore";
	let regex = /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/g
	let email = '';
	let password = '';
	let confirmPassword = '';

	const validarForm = async () => {
		if(!email || !password ||  (password !== confirmPassword)){
			return
		}
		if(email.match(regex) && password === confirmPassword){
			try {
				await authHandlers.signup(email,password)
			} catch (error) {
				console.log(error)
			}
		}
		if($authStore.currentUser){
			window.location.href='/privatedashboard'
		}
	};
</script>

<div class="container mx-auto">
	<h1 class="text-3xl text-center p-5 font-bold">Registrate!</h1>
	<p class="text-center font-semibold">
		Recibe contenido mensualmente y promociones de nuestros servicios.
	</p>
	<form class=" p-10 form-control items-center justify-center">
		<label class="label flex-col items-center w-full max-w-2xl justify-center pb-10">
			<span class="label-text border-b-2 mb-3 self-start font-semibold text-xl">Email</span>
			<input
				bind:value={email}
				type="email"
				placeholder="email@example.com..."
				class="input
            w-full max-w-2xl
            bg-slate-200"
			required
			/>
		</label>
		<label class="label flex-col items-center w-full max-w-2xl justify-center pb-10">
			<span class="label-text border-b-2 mb-3 self-start text-xl font-semibold">Password</span>
			<input
				bind:value={password}
				type="password"
				placeholder="password..."
				class="input
            w-full max-w-2xl
            bg-slate-200"
			/>
		</label>
		<label class="label flex-col items-center w-full max-w-2xl justify-center pb-10">
			<span class="label-text border-b-2 mb-3 self-start text-xl font-semibold"
				>Confirm Password</span
			>
			<input
				bind:value={confirmPassword}
				type="password"
				placeholder="Confirm password..."
				class="input
            w-full max-w-2xl
            bg-slate-200"
			/>
		</label>

		<div class="flex">
			<button
				class="btn text-lg font-semibold btn-sm md:btn-wide btn-warning px-5 mx-2"
				type="reset">Clear</button
			>

			<button class="btn text-lg font-semibold btn-sm md:btn-wide btn-info px-5 mx-2" type="submit"
			on:click={validarForm}	
			>sign up</button
			>
		</div>
	</form>
</div>
