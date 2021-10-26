<template>
  <div class="hello">
    <div>
      <b-button
        variant="success"
        v-on:click="addListElement()"
        class="rounded-md shadow mt-5 btnn"
      >
        Add New Task</b-button
      >
      <b-button
        variant="danger"
        v-on:click="resetListElement()"
        class="rounded-md shadow mt-5 btnn"
      >
        Remove Tasks</b-button
      >
      <ul v-for="count in counts" :key="count" calss="difflist">
        <!--<li class="difflist mx-5" :id="count">{{count}}</li>-->
        
        <!--<table class="shadow-lg bg-white mx-auto">
  <tr>
    <th class=" bg-primary text-white border text-left px-8 py-4">Company</th>
    <th class=" bg-primary text-white border text-left px-8 py-4">Contact</th>
    <th class=" bg-primary text-white border text-left px-8 py-4">Country</th>
  </tr>
  <tr>
    <td class=" border px-8 py-4">Alfreds Futterkiste</td>
    <td class=" border px-8 py-4">Dante Sparks</td>
    <td class=" border px-8 py-4">Italy</td>
  </tr>
  <tr>
    <td class=" border px-8 py-4">Centro comercial Moctezuma</td>
    <td class=" border px-8 py-4">Neal Garrison</td>
    <td class=" border px-8 py-4">Spain</td>
  </tr>
  <tr>
    <td class=" border px-8 py-4">Ernst Handel</td>
    <td class=" border px-8 py-4">Maggie O'Neill</td>
    <td class=" border px-8 py-4">Austria</td>
  </tr>
</table>-->
        <!--<b-card
    title="Card Title"
    img-src="https://picsum.photos/600/300/?image=25"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2 mx-auto shadow"
  >
    <b-card-text>
      Some quick example text to build on the card title and make up the bulk of the card's content.
    </b-card-text>

    <b-button :id="count" variant="danger" v-on:click="removeElement(count)" class="rounded-md shadow difflist"> Remove </b-button>
  </b-card>-->

        <!--<b-button :id="count" variant="success" v-on:click="markAsDone(count)" class="rounded-md shadow difflist"> Mark as done </b-button>
      <b-button :id="count" variant="danger" v-on:click="removeElement(count)" class="rounded-md shadow difflist"> Remove task </b-button>-->
        <b-input-group prepend="Task" class="mt-3 rounded-md shadow">
          <b-form-input :id="count+'input'" :class="count+'inputclass'"></b-form-input>
          <b-input-group-append>
            <b-button
              variant="outline-success"
              :id="count"
              @click.self="markAsDone(count);"
            >
              Mark as done
            </b-button>
            <b-button
              variant="danger"
              v-on:click="removeElement(count)"
              class="rounded-md shadow btn"
            >
              Remove task
            </b-button>
          </b-input-group-append>
        </b-input-group>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      counts: [],
      isPressed: false
    };
  },
  methods: {
    addListElement() {
      this.count++;
      this.counts.push(this.count);
    },
    removeListElement() {
      if (this.count > 0) {
        this.count--;
        this.counts.pop(this.count);
      } else {
        alert("There are no elements to remove !!!");
      }
    },
    removeElement(num) {
      this.counts.splice(this.counts.indexOf(num), 1);
      this.count = this.counts[this.counts.length - 1];
      if (this.counts <= 0) {
        this.count = 0;
      }
    },
    markAsDone(num) {
      if(document.getElementById(num+"input").style.textDecoration != "line-through"){
        document.getElementById(num+"input").style.textDecoration = "line-through";
        document.getElementById(num+"input").style.color = "red"; 
      }else{
        document.getElementById(num+"input").style.textDecoration = "none";
        document.getElementById(num+"input").style.color = "black";
      }
      
    },
    resetListElement() {
      if (this.count > 0) {
        for (let i = this.counts.length; i > 0; i--) {
          this.counts.pop(this.counts[i]);
          this.count = 0;
        }
      } else {
        alert("There are no tasks to remove !!!");
      }
    }
  }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btnn {
  margin-right: 10px;
}
.difflist {
  list-style-type: none;
  display: inline-block;
}
h3 {
  margin: 40px 0 0;
}
.aotherlist {
  list-style-type: none;
  padding: 0;
}
.otherelement {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
