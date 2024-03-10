<template>
	<div class="inputBox shadow">
		<input type="text" class="" v-model="newTodoItem" @keyup.enter="addTodo">
		<!-- <button @click="addTodo">add</button> -->
		<span class="addContainer" @click="addTodo">
			<i class="fa fa-plus addBtn"></i>
		</span>
		<Modal :show="showModal" @close="showModal = false">
      <template #header>
        <h3>
					<span>경고!</span>
					<span class="closeModalBtn" @click="showModal = false"><i class=" fa-solid fa-xmark"></i></span>
				</h3>
      </template>
      <template #body>
        <span>아무것도 입력하지 않으셨습니다.</span>
      </template>
      <template #footer>
        <h3>copyright</h3>
      </template>
    </Modal>
	</div>
</template>

<script>
import Modal from './common/Modal.vue'
export default {
	data() {
		return {
			showModal: false,
			newTodoItem: ''
		}
	},
	methods: {
		addTodo() {
			if (this.newTodoItem !== '') {
				this.$emit('addTodoItem', this.newTodoItem)
				this.clearInput()
			} else {
				this.showModal = !this.showModal
			}
		},
		clearInput() {
			this.newTodoItem = ''
		}
	},
	components: {
		Modal
	}
}
</script>

<style scoped>
input:focus {
	outline: none;
}
.inputBox {
	background: white;
	height: 50px;
	line-height: 50px;
	border-radius: 5px;
}
.inputBox input {
	border-style: none;
	font-size: 0.9rem;
}
.addContainer {
	float: right;
	background: linear-gradient(to right, #6478fb, #8763fb);
	display: block;
	width: 3rem;
	border-radius: 0 5px 5px 0;
	cursor: pointer;
}
.addBtn {
	color: white;
	vertical-align: middle;
}
.closeModalBtn {
	color: #42b983;
	cursor: pointer;
}
</style>