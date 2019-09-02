<template>
  <div>

  <!-- ======== @Region: #highlighted ======== -->
  <div id="pricing" class="bg-light py-3 py-lg-6">
      <div class="container">
        <hr class="hr-lg mt-0 mb-3 w-10 mx-auto hr-primary" />
        <h2 class="text-center text-uppercase font-weight-bold my-0">
          Pricing Plans
        </h2>
        <h5 class="text-center font-weight-light mt-2 mb-0 text-muted">
          Competitive pricing plans to suit your needs
        </h5>
        <hr class="mb-5 w-50 mx-auto" />
        <div class="row pricing-stack">
          <div class="col-md-3" v-for="gym in gyms">
            <div class="card bg-shadow text-center border-0">
              <h4 class="card-title py-3 my-0 text-shadow op-8">
                {{gym.name}}
              </h4>
            
              <div class="card-body">
                <ul class="list-unstyled text-sm text-black-50">
                  <li> {{gym.address}} </li>
                </ul>
                <a href="#" class="btn btn-primary btn-rounded btn-lg">Sign Up</a>
              </div>
            </div>
          </div>
          
          
          
        </div>
        <!-- Plan features -->
        <div class="bg-white bg-op-4 bg-shadow py-3 mt-4 text-center">
          <h5 class="d-inline-block pr-1 my-0">
            All Plans Include:
          </h5>
          <p class="d-inline-block text-black-50 my-0">90 day money back guarantee <span class="text-primary font-weight-bold mx-2">//</span> 24/7 telephone support <span class="text-primary font-weight-bold mx-2">//</span> FREE Setup <span class="text-primary font-weight-bold mx-2">//</span> Migration
            Help <span class="text-primary font-weight-bold mx-2">//</span> Developer API</p>
        </div>
      </div>
    </div>

  <!-- ======== @Region: #content ======== -->
  <div id="content" class="p-0">
    <!-- Features -->
    <div id="features" class="container py-4 py-lg-6">
      <hr class="hr-lg mt-0 mb-3 w-10 mx-auto hr-primary" />
      <h2 class="text-center text-uppercase font-weight-bold my-0">
        Core Features
      </h2>
      <h5 class="text-center font-weight-light mt-2 mb-0 text-muted">
        Great features, great product!
      </h5>
      <hr class="mb-5 w-50 mx-auto" />
      <div class="row text-center">
        <div class="col-lg-4 py-1">
          <i class="la la-tachometer icon-3x text-primary" data-animate="fadeIn" data-animate-delay="0.1"></i>
          <h5 class="mt-1 op-8">
            Fully Optimized
          </h5>
          <p class="text-sm text-black-50">Comis facilisi pala praemitto qui veniam. Erat ex metuo nibh nutus pertineo sagaciter torqueo.</p>
        </div>
        <div class="col-lg-4 py-1">
          <i class="la la-wrench icon-3x text-primary" data-animate="fadeIn" data-animate-delay="0.2"></i>
          <h5 class="mt-1 op-8">
            Free Support
          </h5>
          <p class="text-sm text-black-50">Amet conventio huic secundum torqueo. Gilvus molior plaga quadrum scisco sudo vel venio virtus volutpat.</p>
        </div>
        <div class="col-lg-4 py-1">
          <i class="la la-rocket icon-3x text-primary" data-animate="fadeIn" data-animate-delay="0.3"></i>
          <h5 class="mt-1 op-8">
            Free Upgrades
          </h5>
          <p class="text-sm text-black-50">Appellatio diam esse gemino humo iusto neque nutus.</p>
        </div>
        <div class="col-lg-4 py-1">
          <i class="la la-area-chart icon-3x text-primary" data-animate="fadeIn" data-animate-delay="0.4"></i>
          <h5 class="mt-1 op-8">
            99.9% Uptime
          </h5>
          <p class="text-sm text-black-50">Enim imputo oppeto. Amet camur defui gilvus huic tincidunt velit.</p>
        </div>
        <div class="col-lg-4 py-1">
          <i class="la la-users icon-3x text-primary" data-animate="fadeIn" data-animate-delay="0.5"></i>
          <h5 class="mt-1 op-8">
            Multiuser
          </h5>
          <p class="text-sm text-black-50">Camur capto esse genitus ludus natu occuro vereor vero virtus.</p>
        </div>
        <div class="col-lg-4 py-1">
          <i class="la la-plug icon-3x text-primary" data-animate="fadeIn" data-animate-delay="0.6"></i>
          <h5 class="mt-1 op-8">
            Plug n play
          </h5>
          <p class="text-sm text-black-50">Eros exerci magna. Cogo facilisis humo iustum lenis obruo occuro persto proprius.</p>
        </div>
      </div>
    </div>
        <!--Pricing Table-->
    
    <!-- Steps -->
    
    
    <!--Customer testimonial-->

  </div>

  <!-- ======== @Region: #content-below ======== -->

</div>

 <!--  <div class="container"> -->
<!-- 
    <h1>All Gyms</h1>
    <div v-for="gym in gyms">
      <h2>{{ gym.name }}</h2>
      <p>address: {{ gym.address }}</p>
      <p> ------------------------------------------------------- </p>
    </div>
  </div> -->

    
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      gyms: [],
      open_gym_times: []
    };
  },
  created: function() {
    axios.get("/api/gyms").then(response => {
      this.gyms = response.data;
      console.log(response.data)
    });
  },
  methods: {}
};
</script>

<!-- 
DEBUG THE ALL GYMS FRONTEND!!!!!! THEN, CHECK TRELLO FOR NEXT DUTIES -->