<template>
	<ValidationObserver
		ref="observer"
		v-slot="{ invalid }"
	>
		<form @submit.prevent="submit">
			<ValidationProvider
				v-slot="{ errors }"
				name="Name"
				rules="required|max:10"
			>
				<v-text-field
					v-model="name"
					:counter="10"
					:error-messages="errors"
					label="Name"
					required
				></v-text-field>
			</ValidationProvider>
			<ValidationProvider
				v-slot="{ errors }"
				name="email"
				rules="required|email"
			>
				<v-text-field
					v-model="email"
					:error-messages="errors"
					label="E-mail"
					required
				></v-text-field>
			</ValidationProvider>

			<v-btn
				class="mr-4"
				type="submit"
				:disabled="invalid"
			>
				submit
			</v-btn>
		</form>
	</ValidationObserver>
</template>

<script>
export default {
	name:'login',
	data() {
		return {
			name: '',
			email: ''
		}
	},
	methods:{
		submit(){
			return true
		}
	}
}
</script>

<style scoped>

</style>
