<template>
  <div class="container-fluid py-4">
    <div class="row">
      <div class="col-12">
        <div class="card my-4">
          <div class="card-header p-0 position-relative mt-n4 mx-3 z-index-2">
            <div
              class="bg-gradient-success shadow-success border-radius-lg pt-4 pb-3"
            >
              <h6 class="text-white text-capitalize ps-3">Finger tlqkf</h6>
            </div>
          </div>
          <div class="card-body px-0 pb-2">
            <div class="button">
              <div class="mx-3">
                <a
                class="btn mt-4 w-100"
                :class="`bg-gradient-${this.$store.state.color}`"
                >Translate
                </a>
              </div>
            </div>

            <MaterialInput id="corePoolSize" :value="words" />
            
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import ThreadPoolEditCard from "./components/ThreadPoolEditCard.vue";
import MaterialInput from "@/components/MaterialInput.vue";

export default {
  name: "flows",
  data() {
    return {
      errors: [],
      modal: false,
      messageTitle: "",
      message: "",

      words: "",
      threadPool: {}
    };
  },
  mounted() {
    this.initLoad();
  },
  methods: {
    initLoad() {
    	axios.get('api/templates/flows')
        .then(response => (response.data))
        .then(result => {
          // JSON responses are automatically parsed.
          this.threadPool = result[0].threadPool;
          console.log(this.threadPool);
        })
        .catch(e => {
          this.errors.push(e)
        })
	  }
  },
  components: {
    ThreadPoolEditCard,
    MaterialInput
  },
  
};
</script>
