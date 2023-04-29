<template>
  <div>
    <form @submit.prevent="addPerson">
      <label>
        Name:
        <input type="text" v-model="newPerson.name" />
      </label>
      <label>
        Age:
        <input type="number" v-model.number="newPerson.age" />
      </label>
      <button type="submit">Add Person</button>
    </form>

    <ul>
      <li v-for="(person, index) in people" :key="index">
        {{ person.name }} - {{ person.age }}
        <button @click="deletePerson(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      people: [
        { name: "John", age: 25 },
        { name: "Jane", age: 30 },
      ],
      newPerson: {
        name: "",
        age: null,
      },
    };
  },
methods: {
    addPerson() {
      this.people.push({
        name: this.newPerson.name,
        age: this.newPerson.age,
      });
      this.newPerson.name = "";
      this.newPerson.age = null;
    },
    deletePerson(index) {
      this.people.splice(index, 1);
    },
  },
};
// Example usage:
app.addPerson(); // Prompts the user for input and adds a new person to the array
app.deletePerson(); // Prompts the user for input and deletes a person from the array
console.log(app.people); // Logs the updated array to the console
</script>
