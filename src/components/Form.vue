<template>
	<form class="form" @submit.prevent="submit">
		<div class="form__progress">
			<div class="form__progress--bar" v-for="idx in 6" :key="idx">
				<div v-show="idx < stage"></div>
			</div>
		</div>
		<div class="form__content">
			<div class="form__title">{{ titles[stage-1] }}</div>
			<InputRadio class="form__options" v-if="!finalStage" :options="options[stage]" @input="handleInput" :key="stage" :selected="answers[stage]" />
			<RegForm v-else class="form__register" @update="update" @input="regInput" />
		</div>
		<div class="form__btns">
			<button type="button" class="btn back" v-show="stage > 1" @click="stage--">Назад</button>
			<button type="button" class="btn forward" v-show="!finalStage" @click="stage++">{{ btnText }}</button>
			<button type="submit" class="btn submit" v-show="finalStage">Зарегистрироваться</button>
		</div>
	</form>
</template>

<script>
import options from '../assets/options'

export default {
	name: 'VForm',
	components: {
		InputRadio: () => import('./InputRadio.vue'),
		RegForm: () => import('./RegForm.vue')
	},
	data: () => ({
		answers: {
			1: options[1][0],
			2: options[2][0],
			3: options[3][0],
			4: options[4][0],
			5: options[5][0],
			6: options[6][0],
			name: '',
			email: '',
			tel: '',
			code: ''
		},
		options,
		titles: [
			'Из какой вы страны?',
			'Сколько вам лет?',
			'В какой сфере сейчас работаете?',
			'Ваш средний доход в месяц',
			'Рассматриваете ли в перспективе платное обучение профессии Разработчик Искусственного Интеллекта?',
			'Сколько времени готовы выделить на обучение в неделю?',
			'Зарегистрироваться'
		],
		stage: 1
	}),
	computed: {
		btnText() {
			if (this.stage === 6) return 'К последнему'
			return 'Вперёд'
		},
		finalStage() {
			return this.stage === 7
		}
	},
	methods: {
		submit() {
			window.location.href = 'https://neural-university.ru/thank_you'
		},
		handleInput(input) {
			this.answers[this.stage] = input
		},
		update(e) {
			this.answers.tel = e.tel
			this.answers.code = e.code
		},
		regInput(e) {
			this.answers[e.type] = e.value
		}
	}
}
</script>

<style lang="scss" scoped>
.form {
	width: 100%;
	position: relative;
	display: flex;
	flex-direction: column;
	padding: 8px 0;
	gap: 30px;
	min-height: 511px;
	background: no-repeat url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4gPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHByZXNlcnZlQXNwZWN0UmF0aW89Im5vbmUiIHdpZHRoPSI2MDAiIGhlaWdodD0iNTExIiB2aWV3Qm94PSIwIDAgNjAwIDUxMSIgZmlsbD0ibm9uZSI+IDxwYXRoIGQ9Ik0wLjUgMzkuMTUxNUMwLjUgMzguMjMyIDAuODYxODEyIDM3LjM0OTUgMS41MDcyMyAzNi42OTQ3TDM0LjE4MTEgMy41NDMxNUMzNC44Mzg5IDIuODc1NzYgMzUuNzM2OCAyLjUgMzYuNjczOSAyLjVINTIxLjg5OEM1MjIuNzk4IDIuNSA1MjMuNjYzIDIuODQ2NjIgNTI0LjMxNCAzLjQ2Nzg3TDUyNC42NTkgMy4xMDYxNUw1MjQuMzE0IDMuNDY3ODhMNTk4LjQxNiA3NC4xNzk5QzU5OS4xMDggNzQuODQwMyA1OTkuNSA3NS43NTUzIDU5OS41IDc2LjcxMlY1MDdDNTk5LjUgNTA4LjkzMyA1OTcuOTMzIDUxMC41IDU5NiA1MTAuNUgyNDQuMTkzQzI0My4yNDYgNTEwLjUgMjQyLjM0IDUxMC4xMTYgMjQxLjY4IDUwOS40MzZMMjAwLjAzOCA0NjYuNDkxQzE5OS4xOSA0NjUuNjE3IDE5OC4wMjQgNDY1LjEyNCAxOTYuODA3IDQ2NS4xMjRINEMyLjA2NyA0NjUuMTI0IDAuNSA0NjMuNTU3IDAuNSA0NjEuNjI0VjM5LjE1MTVaIiBmaWxsPSIjMkI1Mjc4IiBmaWxsLW9wYWNpdHk9IjAuMiIgc3Ryb2tlPSIjNjVCOUY0Ij48L3BhdGg+IDxwYXRoIGQ9Ik01OTkuNSA2Mi44NTQzTDUzMi4yNzQgMC41SDU5NkM1OTcuOTMzIDAuNSA1OTkuNSAyLjA2NyA1OTkuNSA0VjYyLjg1NDNaIiBmaWxsPSIjMkI1Mjc4IiBzdHJva2U9IiM2NUI5RjQiPjwvcGF0aD4gPC9zdmc+IA==');
	background-size: 100% 100%;
	&__content {
		flex-grow: 1;
		padding: 0 40px;
	}
	&__title {
		color: #dfe6ed;
		font-size: 24px;
		margin-bottom: 30px;
	}
	&__progress {
		height: 8px;
		display: flex;
		gap: 5px;
		margin: 0 13% 0 7%;
		&--bar {
			border: 1px solid #65B9F4;
			flex-grow: 1;
			div {
				background: #65B9F4;
				height: 100%;
			}
		}
	}
	img {
		width: 100%;
		display: block;
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
	}
	&__btns {
		margin: auto;
		margin-right: 10px;
		display: flex;
		justify-content: flex-end;
	}
	.btn {
		border: none;
		background: none;
		font-size: 100%;
		font-family: inherit;
		flex: 1 0 175px;
		height: 44px;
		padding: 0;
		cursor: pointer;
		&.forward, &.submit {
			background: no-repeat url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4gPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNzIiIGhlaWdodD0iNDQiIHZpZXdCb3g9IjAgMCAxNzIgNDQiIGZpbGw9Im5vbmUiPiA8cGF0aCBkPSJNMTcyIDQ0TDE1LjgzMjYgNDRMNS43NTczMiAzMFY4TC00LjA1MzEyZS0wNiAwTDExMS45MDggMEwxMTUuODY2IDUuNUwxNjMuMzY0IDUuNUwxNzIgMTcuNVY0NFoiIGZpbGw9IiM2NUI5RjQiPjwvcGF0aD4gPC9zdmc+IA==');
		}
		&.back {
			color: #65B9F4;
			background: no-repeat url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4gPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNzUiIGhlaWdodD0iNDQiIHZpZXdCb3g9IjAgMCAxNzUgNDQiIGZpbGw9Im5vbmUiPiA8cGF0aCBkPSJNOC45Nzc5MSA0MC41TDAuNSAyOC42ODMzVjIuNUgzOS4xMDkxVjQwLjVIOC45Nzc5MVoiIGZpbGw9IiM2NUI5RjQiIHN0cm9rZT0iIzY1QjlGNCI+PC9wYXRoPiA8cGF0aCBkPSJNNjAuMjE0MiAzOC4yMDkxTDYwLjA2NDYgMzhINTkuODA3NUgxMi44NDI4TDQuNSAyNi4zMzk1VjAuNUgxNTkuMDAyTDE2OC43NzYgMTQuMTYwNVYzNlYzNi4xNjA0TDE2OC44NyAzNi4yOTA5TDE3NC4wMjcgNDMuNUg2My45OTk3TDYwLjIxNDIgMzguMjA5MVoiIGZpbGw9IiMxQjJCM0EiIHN0cm9rZT0iIzY1QjlGNCI+PC9wYXRoPiA8L3N2Zz4g');
		}
		&.submit {
			font-size: 16px;
		}
	}
}

@media (max-width: 640px) {
	.form {
		background: no-repeat url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4gPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHByZXNlcnZlQXNwZWN0UmF0aW89Im5vbmUiIHdpZHRoPSIzMDEiIGhlaWdodD0iMzcyIiB2aWV3Qm94PSIwIDAgMzAxIDM3MiIgZmlsbD0ibm9uZSI+IDxwYXRoIGQ9Ik0wLjUgMjcuMTc5NEMwLjUgMjYuNDgwMyAwLjcwOTM1NSAyNS43OTczIDEuMTAxMDkgMjUuMjE4MkwxNi43ODI3IDIuMDM4OEwxNi4zNjg2IDEuNzU4NjJMMTYuNzgyNyAyLjAzODc5QzE3LjQzMzcgMS4wNzY1MSAxOC41MTk4IDAuNSAxOS42ODE2IDAuNUgyNjAuNTcyQzI2MS42OTkgMC41IDI2Mi43NTYgMS4wNDE5NCAyNjMuNDE0IDEuOTU2MThMMjk5Ljg0MSA1Mi41OTcxQzMwMC4yNyA1My4xOTI1IDMwMC41IDUzLjkwNzQgMzAwLjUgNTQuNjQwOVYzNjhDMzAwLjUgMzY5LjkzMyAyOTguOTMzIDM3MS41IDI5NyAzNzEuNUgxMjEuNjU0SDRDMi4wNjcwMSAzNzEuNSAwLjUgMzY5LjkzMyAwLjUgMzY4VjI3LjE3OTRaIiBmaWxsPSIjMkI1Mjc4IiBmaWxsLW9wYWNpdHk9IjAuMiIgc3Ryb2tlPSIjNjVCOUY0Ij48L3BhdGg+IDxwYXRoIGQ9Ik0zMDAgMzguOTU4NUwyNzIuNDggMUgyOTYuNUMyOTguNDMzIDEgMzAwIDIuNTY3IDMwMCA0LjVWMzguOTU4NVoiIGZpbGw9IiMyQjUyNzgiIHN0cm9rZT0iIzY1QjlGNCI+PC9wYXRoPiA8L3N2Zz4g');
		background-size: 100% 100%;
		&__btns {
			justify-content: center;
			margin: auto;
			transform: scale(80%);
		}
	}
}

@media (max-width: 550px) {
	.form__content {
		padding: 0 20px;
	}
}
</style>