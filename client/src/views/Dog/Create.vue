<template>
	<div class="lg:px-48 md:px-32 xl:px-64">
		<div class="text-bluegray-700 text-2xl border-b-2 border-bluegray-200 pb-3">
			Create
		</div>

		<!-- input fields -->

		<div class="mt-5 min-w-full">
			<form @submit.prevent="postDog">
				<!-- name -->
				<div class="grid grid-cols-1 lg:grid-cols-2 sm:gap-4 gap-y-4">
					<div>
						<div class="text-xl text-bluegray-700">Name</div>
						<input
							type="text"
							name=""
							id=""
							class="w-full px-4 py-2 rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.dog_name"
						/>
					</div>

					<!-- breed -->
					<div>
						<div class="text-xl text-bluegray-700">Breed</div>
						<input
							type="text"
							name=""
							id=""
							class="w-full px-4 py-2 rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.breed"
						/>
					</div>

					<!-- date of birth -->
					<div>
						<div class="text-xl text-bluegray-700">Date of Birth</div>
						<input
							type="date"
							name=""
							id=""
							class="w-full px-4 py-2 rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.birthday"
						/>
					</div>

					<!-- sex -->
					<div>
						<div class="text-xl text-bluegray-700">Sex</div>
						<select
							name=""
							id=""
							class="w-full px-4 py-3 text-sm rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.sex"
						>
							<option value="">Male</option>
							<option value="">Female</option>
						</select>
					</div>

					<!-- weight -->
					<div>
						<div class="text-xl text-bluegray-700">Weight in kg</div>
						<input
							type="number"
							name=""
							id=""
							step="0.01"
							class="w-full px-4 py-2 rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.weight"
						/>
					</div>

					<!-- marks -->
					<div>
						<div class="text-xl text-bluegray-700">Marks</div>
						<input
							type="text"
							name=""
							id=""
							class="w-full px-4 py-2 rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.marks"
						/>
					</div>

					<!-- color -->
					<div>
						<div class="text-xl text-bluegray-700">Color/s</div>
						<input
							type="text"
							name=""
							id=""
							class="w-full px-4 py-2 rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.color"
						/>
					</div>

					<!-- status -->
					<div>
						<div class="text-xl text-bluegray-700">Status</div>
						<select
							name=""
							id=""
							class="w-full px-4 py-3 text-sm rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.status"
						>
							<option value="">Adopted</option>
							<option value="">Inactive</option>
							<option value="">Recuperating</option>
							<option value="">Transferred</option>
							<option value="">Healthy</option>
						</select>
					</div>

					<!-- aggressive -->
					<div>
						<div class="text-xl text-bluegray-700">Aggressive?</div>
						<select
							name=""
							id=""
							class="w-full px-4 py-3 text-sm rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.aggressive"
						>
							<option value="">No</option>
							<option value="">Yes</option>
						</select>
					</div>

					<!-- trained -->
					<div>
						<div class="text-xl text-bluegray-700">Trained?</div>
						<select
							name=""
							id=""
							class="w-full px-4 py-3 text-sm rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
							v-model="dog.trained"
						>
							<option value="">No</option>
							<option value="">Yes</option>
						</select>
					</div>
				</div>

				<!-- description -->
				<div class="mt-4">
					<div class="text-xl text-bluegray-700">Description</div>
					<textarea
						name=""
						id=""
						class="w-full px-4 py-3 text-sm rounded focus:outline-none focus:ring-2 focus:ring-bluegray-700"
						v-model="dog.description"
					></textarea>
				</div>

				<!-- file upload -->
				<!-- <div class="mt-4">
					<div class="text-bluegray-700">
						<input id="fileUpload" type="file" hidden multiple />
						<button
							@click="chooseFiles()"
							class="w-full flex justify-center items-center px-4 py-4 rounded border-2 border-bluegray-700 border-dashed"
						>
							<upload-icon size="1.5x" class="mr-2"></upload-icon>
							Upload Images
						</button>
					</div>
				</div> -->

				<div class="flex justify-end space-x-3 mt-5">
					<button class="btn-secondary px-4 py-2">Cancel</button>
					<button class="btn-primary px-4 py-2">Create</button>
				</div>
			</form>
		</div>
	</div>
</template>

<script>
	import { UploadIcon, Tren } from "vue-feather-icons";
	import DogService from '../../Services/DogService'
	export default {
		components: {
			UploadIcon,
		},
		data(){
			return{
				dog: {
					dog_name: '',
			breed: '',
			birthday: '',
			sex: '',
			weight: '',
			color: '',
			marks: '',
			aggressive: '',
			trained: '',
			status: '',
			table_status: '',
			description: '',
				}
			}
		},
		methods: {
			// chooseFiles() {
			// 	document.getElementById("fileUpload").click();
			// },

			async postDog() {
				// insert input error handling here
				try{
					await DogService.postDog(this.dog)
				}catch(error) {
					console.error(error.message)
				}
			}
		},
	};
</script>

<style>
</style>