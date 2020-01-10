<template>
  <div>
    <transition name="modal">
      <div id="modalContainer" v-if="isOpen">
        <div class="overlay" @click.self="isOpen = false;">
          <div class="modal">
            <h1>Create New Habit</h1>
            <p>Discipline in a man shows determination.</p>
            <form @submit="addHabit">
				<input type="text" v-model="title" name="title" placeholder="add habit...">
				<input type="submit" value="Add" class="btn">
			</form>
          </div>
        </div>
      </div>
    </transition>
    <button @click="isOpen = !isOpen;">
      {{ isOpen ? "Close" : "Add" }} Habit
    </button>
  </div>
</template>

<script>
export default {
	data: function() {
		return {
			isOpen: false
		};
	},
	methods: {
		addHabit(e){
			e.preventDefault();
			const newHabit = {
				title: this.title,
				completed: false
			}

			//Send upto the parent
			this.$emit('add-habit', newHabit);
			this.title = '';

			}
		}
};
</script>

<style scoped>
.modal {
  width: 500px;
  margin: 0px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px 3px;
  transition: all 0.2s ease-in;
  font-family: Helvetica, Arial, sans-serif;
}
.fadeIn-enter {
  opacity: 0;
}

.fadeIn-leave-active {
  opacity: 0;
  transition: all 0.2s step-end;
}

.fadeIn-enter .modal,
.fadeIn-leave-active.modal {
  transform: scale(1.1);
}
button {
  padding: 7px;
  margin: 10px;
  background-color: green;
  color: white;
  font-size: 1.1rem;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #00000094;
  z-index: 999;
  transition: opacity 0.2s ease;
}

input[type="text"] {
	padding: 5px;
}
input[type="submit"] {
}
</style>
