<template>
	<div class="reg">
		<label class="label">
			<span>Имя</span>
			<input type="text" placeholder="Александр" required @input="input('name', $event)">
		</label>
		<label class="label">
			<span>Email</span>
			<input type="email" placeholder="example@gmail.com" required @input="input('email', $event)">
		</label>
		<label class="label">
			<span>Телефон</span>
			<VuePhoneNumberInput v-model="tel" :required="true" :border-radius="0" :translations="i18n" @update="update" />
		</label>
		<p class="policy"> Нажимая кнопку, я даю согласие на обработку персональных данных и соглашаюсь c <a href="https://neural-university.ru/policy">политикой конфиденциальности</a> и договором оферты</p>
	</div>
</template>

<script>
import 'vue-phone-number-input/dist/vue-phone-number-input.css';

export default {
	name: 'reg-form',
	components: {
		VuePhoneNumberInput: () => import('vue-phone-number-input')
	},
	data: () => ({
		tel: '',
		code: '',
		i18n: {
			example: 'Пример',
			phoneNumberLabel: '(999) 999-99-99',
			countrySelectorLabel: 'Код страны'
		}
	}),
	methods: {
		update(e) {
			this.$emit('update', { tel: e.phoneNumber, code: e.countryCode })
		},
		input(type, e) {
			this.$emit('input', { type, value: e.target.value })
		}
	}
}
</script>

<style lang="scss" scoped>
.reg {
	display: flex;
	flex-direction: column;
	gap: 20px;
	.label {
		display: flex;
		flex-direction: column;
		color: #a7bed3;
		font-size: 18px;
		gap: 10px;
		input {
			height: 30px;
			background: none;
			border: none;
			color: inherit;
			font: inherit;
			font-size: 14px;
			border-bottom: 1px solid #ff9e5e;
		}
	}
	.policy {
		color: #395e94;
		font-size: 13px;
		a {
			color: inherit;
			text-decoration: underline;
		}
	}
}

.country-selector__input {
	background: none;
	border: none;
}
</style>