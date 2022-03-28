<template>
	<AppLayout>
		<div class="max-w-[940px] mx-auto w-full flex flex-col gap-y-6">
			<div class="flex gap-x-4">
				<PrimaryButton>Button</PrimaryButton
				><PrimaryButton :disabled="true">Button</PrimaryButton>
			</div>
			<div class="flex gap-x-4">
				<OutlinedButton /> <OutlinedButton :disabled="true" />
			</div>
			<form
				@submit.prevent="onSubmit"
				class="border-[1px] border-neutral-300 rounded w-full p-4 flex flex-col"
			>
				<div class="flex flex-col text-left">
					<!-- NOTE: style yout text field component here -->
					<input
						type="text"
						placeholder="enter your name"
						v-model="text"
						class="border-neutral-300 outline-0 border-[1px] h-10 w-full px-4 placeholder-neutral-300 max-w-[320px] focus:border-primary-500"
						:class="[
							this.text.length !== 0 && 'border-secondary-500',
							this.error && 'border-error-500',
						]"
					/>
					<div class="min-h-[24px]">
						<span v-if="error" class="text-error-500 text-xs"
							>this field is required.</span
						>
					</div>

					<input
						type="text"
						placeholder="enter your name"
						disabled
						class="border-neutral-300 outline-0 border-[1px] h-10 w-full px-4 placeholder-neutral-300 disabled:bg-neutral-100 max-w-[320px]"
					/>
				</div>

				<div class="mt-4">
					<PrimaryButton :disabled="this.error">submit</PrimaryButton>
				</div>
			</form>
			<div
				class="border-[1px] md:max-w-[493px] lg:max-w-full border-neutral-300 rounded-lg py-6 px-[30px] md:px-12 lg:flex"
			>
				<div
					class="md:justify-center lg:justify-start md:flex text-center md:items-center md:text-left w-full"
				>
					<img
						:src="jiramed"
						class="rounded-[50%] h-[120px] w-[120px] mx-auto mb-6 md:m-0 md:mr-[34px]"
					/>
					<div>
						<p class="text-neutral-900 text-xl leading-[17px] mb-[14px]">
							Firstname Lastname
						</p>
						<p class="text-neutral-500 text-sm leading-[17px] text-end">
							Software Engineer
						</p>
					</div>
				</div>

				<hr
					class="w-full mx-auto border-t-[1px] border-neutral-100 my-4 lg:hidden"
				/>
				<div class="lg:border-l-[1px] lg:border-neutral-100 lg:pl-[72px]">
					<div
						class="flex flex-wrap gap-2 lg:gap-x-2 lg:gap-y-[10px] lg:w-[208px]"
					>
						<SkillBadge class="bg-badge-html text-white">HTML</SkillBadge>
						<SkillBadge class="bg-badge-js">JavaScript</SkillBadge>
						<SkillBadge class="bg-badge-vue text-white">Vue</SkillBadge>
						<SkillBadge class="bg-secondary-300 text-white"
							>Web design</SkillBadge
						>
						<SkillBadge class="bg-primary-500 text-white">Figma</SkillBadge>
					</div>
				</div>
			</div>
		</div>
	</AppLayout>
</template>

<script>
import AppLayout from "@/layout/AppLayout";
import PrimaryButton from "@/components/PrimaryButton";
import OutlinedButton from "@/components/OutlinedButton";
import SkillBadge from "@/components/SkillBadge.vue";

export default {
	name: "HappyHacking",
	components: { AppLayout, PrimaryButton, OutlinedButton, SkillBadge },
	data() {
		return {
			text: "",
			error: false,
			jiramed: require("@/assets/jiramed.png"),
		};
	},
	methods: {
		onSubmit() {
			if (this.text === "" || !this.text) {
				this.error = true;
			} else {
				const yourName = {
					name: this.text,
				};

				alert(JSON.stringify(yourName, null, 2));
			}
		},
	},
	watch: {
		text: function (val) {
			console.log("val", val);
			this.error = false;
		},
	},
};
</script>
