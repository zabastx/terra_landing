<template>
	<section class="intro">
		<div class="date">29 ноября в 19:00 МСК</div>
		<h1 class="heading"> ДЕНЬ ОТКРЫТЫХ ДВЕРЕЙ В УНИВЕРСИТЕТЕ ИСКУССТВЕННОГО ИНТЕЛЛЕКТА</h1>
		<p>Стань AI разработчиком, зарабатывай от 150К в месяц и создай свой AI проект</p>
		<div class="list">
			<div class="list__overlay"></div>
			<li><i class="icon"></i> #Самая_востребованная_профессия</li>
			<li><i class="icon"></i> #Технология_будущего</li>
			<li><i class="icon"></i> #Свой_AI_проект</li>
		</div>
	</section>
</template>

<script>
export default {
	name: 'intro'
}
</script>

<style lang="scss" scoped>
.intro {
	display: flex;
	flex-direction: column;
	gap: 50px;
}

.date {
	font-size: 1.75rem;
	color: #65b9f4;
}

.heading {
	font-size: 2rem;
	color: #ff9e5e;
}

p {
	color: #f2f5fa;
	font-size: 25px;
}

.list {
	margin: 0;
	padding: 0;
	position: relative;
	margin-right: 20px;
	&__overlay {
		position: absolute;
		right: -10px;
		left: 50%;
		top: -10px;
		bottom: -5px;
		background: linear-gradient(to right, #17212b00, #17212bff 40%, #17212bff);
	}
	li {
		height: 47px;
		display: flex;
		align-items: center;
		gap: 10px;
		padding: 10px;
		color: #a7bed3;
		font-size: 20px;
		transition-duration: 300ms;
		margin-bottom: 5px;
		user-select: none;
		background: no-repeat url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4gPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI0MzYiIGhlaWdodD0iNDciIHZpZXdCb3g9IjAgMCA0MzYgNDciIGZpbGw9Im5vbmUiPiA8cGF0aCBkPSJNMSA0MVYxSDQzNS41VjQ2LjVIOS41TDEgNDFaIiBzdHJva2U9IiM2NUI5RjQiPjwvcGF0aD4gPC9zdmc+IA==');
		&:hover {
			box-shadow: 0px 0px 10px 0px #e1fdff4d;
		}
	}
	.icon {
		width: 15px;
		height: 15px;
		display: inline-block;
		border: 1px solid #9DD3F9;
		box-shadow: 0px 0px 10px 0px #e1fdff4d;
		position: relative;
		transform: rotate(45deg);
		&::after {
			content: "";
			width: 7px;
			height: 7px;
			display: inline-block;
			border: 1px solid #9DD3F9;
			position: absolute;
			left: 2px;
			top: 2px;
		}
	}
}
</style>