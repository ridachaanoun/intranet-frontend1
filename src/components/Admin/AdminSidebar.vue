<template>
    <div class="w-64 fixed top-0 bottom-0 bg-surface shadow-lg z-40 overflow-y-auto glass-effect">
      <!-- Dashboard Logo -->
      <div class="px-6 py-6 flex items-center border-b border-background-light">
        <img src="https://ui-avatars.com/api/?name=YouCode&background=00e68c&color=fff" class="h-8 w-8 rounded" alt="YouCode Logo">
        <span class="ml-3 text-xl font-bold text-text-primary">ADMIN PANEL</span>
      </div>
      
      <!-- Admin Info -->
      <div class="p-4 flex items-center space-x-3 mb-4 border-b border-background-light">
        <img 
          src="https://ui-avatars.com/api/?name=Admin&background=ff5c2b&color=fff" 
          class="w-10 h-10 rounded-full border-2 border-secondary-500"
          alt="Admin Profile"
        >
        <div>
          <h3 class="font-medium text-text-primary">{{ currentUser }}</h3>
          <p class="text-xs text-text-muted">Administrator</p>
        </div>
      </div>
      
      <!-- Navigation -->
      <nav class="px-4">
        <div class="mb-6">
          <h6 class="text-xs uppercase text-text-muted font-semibold px-3 mb-2">Management</h6>
          
          <a 
            href="#" 
            @click.prevent="$emit('change-section', 'dashboard')" 
            :class="{'bg-background-element shadow-soft glow-on-hover': activeSection === 'dashboard'}" 
            class="flex items-center py-3 px-3 mb-1 rounded-lg text-text-primary hover:bg-surface-hover group transition-colors"
          >
            <i class="fas fa-tachometer-alt w-6 text-center text-lg" :class="{'text-accent-400': activeSection === 'dashboard'}"></i>
            <span class="ml-3">Dashboard</span>
          </a>
          
          <a 
            href="#" 
            @click.prevent="$emit('change-section', 'users')" 
            :class="{'bg-background-element shadow-soft glow-on-hover': activeSection === 'users'}" 
            class="flex items-center py-3 px-3 mb-1 rounded-lg text-text-primary hover:bg-surface-hover group transition-colors"
          >
            <i class="fas fa-users w-6 text-center text-lg" :class="{'text-accent-400': activeSection === 'users'}"></i>
            <span class="ml-3">Users</span>
          </a>
          
          <a 
            href="#" 
            @click.prevent="$emit('change-section', 'classes')" 
            :class="{'bg-background-element shadow-soft glow-on-hover': activeSection === 'classes'}" 
            class="flex items-center py-3 px-3 mb-1 rounded-lg text-text-primary hover:bg-surface-hover group transition-colors"
          >
            <i class="fas fa-chalkboard w-6 text-center text-lg" :class="{'text-accent-400': activeSection === 'classes'}"></i>
            <span class="ml-3">Classes</span>
          </a>
        </div>
        
        <div class="mb-6">
          <h6 class="text-xs uppercase text-text-muted font-semibold px-3 mb-2">System</h6>
          
          <a 
            href="#"
            class="flex items-center py-3 px-3 mb-1 rounded-lg text-text-primary hover:bg-surface-hover group transition-colors"
          >
            <i class="fas fa-cog w-6 text-center text-lg"></i>
            <span class="ml-3">Settings</span>
          </a>
          
          <a 
            href="#" 
            class="flex items-center py-3 px-3 mb-1 rounded-lg text-text-primary hover:bg-surface-hover group transition-colors"
          >
            <i class="fas fa-sign-out-alt w-6 text-center text-lg"></i>
            <span class="ml-3">Logout</span>
          </a>
        </div>
      </nav>
      
      <!-- Current Time at bottom of sidebar -->
      <div class="absolute bottom-4 left-0 right-0 text-center text-xs text-text-muted">
        {{ currentDateTime }}
      </div>
    </div>
  </template>
  
  <script>
  import { computed } from 'vue';
  import { useAppStore } from '@/stores/app';
  
  export default {
    name: 'AdminSidebar',
    props: {
      activeSection: {
        type: String,
        required: true
      }
    },
    emits: ['change-section'],
    setup() {
      const appStore = useAppStore();
      
      const currentUser = computed(() => appStore.currentUser);
      const currentDateTime = computed(() => appStore.currentDateTime);
      
      return {
        currentUser,
        currentDateTime
      };
    }
  };
  </script>