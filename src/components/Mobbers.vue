<template>
  <section>
    <!-- Here the v:on attribute is used, which is used to respond to any event. In this case, when the "click" event happens, it causes the value of showComplete to be changed. It is attached here to the label. -->
    <h4>
        <label v-on:click="showComplete = !showComplete">

            <!-- The v-model attribute causes the checkdness of this box to always mirror the application's state  -->
            <input type="checkbox" v-model="showComplete">
            Show Completed
        </label>
    </h4>

    <!-- This list group contains a Vue repeater.-->
    <ul class="list-group">
        <!-- The v-for attribute that we see here repeats whatever tag it is on (in this case, a LI) one time for each element of the referenced list, which in this case is our list. Each repetition, the property has a different value.  -->
        <li v-for="mobber in filteredMob" class="list-group-item" v-on:click="mobber.complete = !mobber.complete;" :key="mobber.name">
            <label class="form-check-label ml-4">
                <input
                  type="checkbox"
                  v-model="mobber.complete"
                  class="form-check-input">
                <!-- v-bind is used to change the value of HTML attributes, in this case the class attribute. -->
                <span
                  class="capitalize"
                  v-bind:class="{completed:mobber.complete}">

                  <!-- Here we see an example of Vue's {{ }} syntax, which is quite familiar to any Angular or Handlebars users.-->
                  {{ mobber.name }}
                </span>
            </label>
            <span class="close" v-on:click="removeMobber(mobber)">
              <i class="far fa-times-circle"></i>
            </span>
        </li>
    </ul>

    <!-- Here, a form is used to contain the submit button (which allows keyboard input to be captured.) Notice the v-on directive being used. The .prevent method works the same as submit, but also prevents the default behavior. -->
    <form v-on:submit.prevent="addMobber" class="mt-3">
        <input
          type="text"
          v-model="text"
          class="form-control"
          placeholder="Add a Driver">

        <!-- Note the property :disabled. It begins with a colon (:), indicating that Vue should interpret the value as an expression, and not a string.-->
        <button
          :disabled="submitIsDisabled"
          class="btn btn-primary mt-2">
          Add Driver
        </button>
    </form>
  </section>
</template>

<script>
let mob = [{
  name: "Janean",
  complete: false
},
{
  name:"Aaron",
  complete: false
}];

export default {
  name: 'Mobbers',
  data() {
    return {
      mob,
      text:'',
      showComplete:true,
    };
  },
  computed: {
    filteredMob() {
      return this.mob
      .filter(mobber=>this.showComplete ? true : !mobber.complete);
    },
    submitIsDisabled() {
      return this.text == '';
    }
  },
  methods: {
    addMobber() {
      mob.push({
        name:this.text,
        complete: false
      });
      this.text = '';
    },
    removeMobber(index) {
      this.mob.splice(index, 1)
    }
  }
}
</script>

<style scoped>
  .list-group {
    text-align: left;
  }

  .completed {
    font-style: italic;
    text-decoration: line-through;
    color: gray;
  }

  ul {
      cursor: pointer;
  }

  .capitalize {
    text-transform: capitalize;
  }
</style>