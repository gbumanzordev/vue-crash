<template>
  <form class="add-form" @submit="onSubmit">
    <div class="form-control">
      <label for="text">Task</label>
      <input
        type="text"
        v-model="text"
        id="text"
        name="text"
        placeholder="Add Task"
      />
    </div>
    <div class="form-control">
      <label for="day">Day & Time</label>
      <input
        type="text"
        v-model="day"
        id="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label for="reminder">Set Reminder</label>
      <input type="checkbox" v-model="reminder" id="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      text: '',
      day: '',
      reminder: '',
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.text) {
        alert('Please add a task');
      }

      const newTask = {
        id: Math.floor(Math.random() * 1000000),
        day: this.day,
        text: this.text,
        reminder: this.reminder,
      };

      this.text = '';
      this.day = '';
      this.reminder = false;
      this.$emit('add-task', newTask);
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
