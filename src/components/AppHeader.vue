<script>
import AppNav from "./AppNav.vue";
export default {
  components: {
    AppNav,
  },
};
</script>

<template>
    <header class="fixed-top container-fluid">
        <div class="row row-cols row-cols-md row-cols-sm">
            <div class="contents d-flex justify-content-between px-4 z-1">
                <div class="logo d-flex">
                    <router-link :to="{ name: 'home' }">
                        <div class="text-center">
                            MIXTALES
                        </div>

                    </router-link>
                </div>
  
                <AppNav />

            </div>
        </div>
    </header>
</template>
  