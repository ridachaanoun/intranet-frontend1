<template>
    <div class="admin-dashboard min-h-screen bg-background">
      <!-- Admin Dashboard Layout -->
      <div class="flex">
        <!-- Sidebar -->
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
              <h3 class="font-medium text-text-primary">Admin</h3>
              <p class="text-xs text-text-muted">Administrator</p>
            </div>
          </div>
          
          <!-- Navigation -->
          <nav class="px-4">
            <div class="mb-6">
              <h6 class="text-xs uppercase text-text-muted font-semibold px-3 mb-2">Management</h6>
              
              <a 
                href="#" 
                @click.prevent="activeSection = 'dashboard'" 
                :class="{'bg-background-element shadow-soft glow-on-hover': activeSection === 'dashboard'}" 
                class="flex items-center py-3 px-3 mb-1 rounded-lg text-text-primary hover:bg-surface-hover group transition-colors"
              >
                <i class="fas fa-tachometer-alt w-6 text-center text-lg" :class="{'text-accent-400': activeSection === 'dashboard'}"></i>
                <span class="ml-3">Dashboard</span>
              </a>
              
              <a 
                href="#" 
                @click.prevent="activeSection = 'users'" 
                :class="{'bg-background-element shadow-soft glow-on-hover': activeSection === 'users'}" 
                class="flex items-center py-3 px-3 mb-1 rounded-lg text-text-primary hover:bg-surface-hover group transition-colors"
              >
                <i class="fas fa-users w-6 text-center text-lg" :class="{'text-accent-400': activeSection === 'users'}"></i>
                <span class="ml-3">Users</span>
              </a>
              
              <a 
                href="#" 
                @click.prevent="activeSection = 'classes'" 
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
        </div>
  
        <!-- Main Content -->
        <div class="ml-64 flex-1 p-8">
          <!-- Header Bar -->
          <div class="mb-8 flex justify-between items-center">
            <div>
              <h1 class="text-3xl font-bold text-text-primary">{{ sectionTitle }}</h1>
            </div>
            <div class="flex space-x-4">
              <button class="bg-background-element p-2 rounded-lg text-text-secondary hover:text-accent-400 transition-colors">
                <i class="fas fa-bell"></i>
              </button>
              <button class="bg-background-element p-2 rounded-lg text-text-secondary hover:text-accent-400 transition-colors">
                <i class="fas fa-cog"></i>
              </button>
            </div>
          </div>
  
          <!-- Dashboard Section -->
          <div v-if="activeSection === 'dashboard'" class="fade-in">
            <!-- Stats Overview -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
              <!-- Total Users -->
              <div class="bg-surface rounded-xl p-6 shadow-card glass-effect relative overflow-hidden group card-hover">
                <div class="absolute top-0 right-0 w-24 h-24 -mt-8 -mr-8 rounded-full bg-primary-900/20 group-hover:bg-primary-900/30 transition-all"></div>
                <div class="relative">
                  <div class="text-sm text-text-secondary mb-1">Total Users</div>
                  <div class="text-3xl font-bold text-text-primary mb-2">248</div>
                  <div class="flex items-center text-sm text-accent-400">
                    <i class="fas fa-arrow-up mr-1"></i>
                    <span>12% increase</span>
                  </div>
                </div>
                <div class="absolute bottom-6 right-6 w-12 h-12 rounded-lg bg-primary-500/20 flex items-center justify-center text-primary-400">
                  <i class="fas fa-users text-xl"></i>
                </div>
              </div>
  
              <!-- Total Classes -->
              <div class="bg-surface rounded-xl p-6 shadow-card glass-effect relative overflow-hidden group card-hover">
                <div class="absolute top-0 right-0 w-24 h-24 -mt-8 -mr-8 rounded-full bg-secondary-900/20 group-hover:bg-secondary-900/30 transition-all"></div>
                <div class="relative">
                  <div class="text-sm text-text-secondary mb-1">Total Classes</div>
                  <div class="text-3xl font-bold text-text-primary mb-2">12</div>
                  <div class="flex items-center text-sm text-accent-400">
                    <i class="fas fa-arrow-up mr-1"></i>
                    <span>3 new classes</span>
                  </div>
                </div>
                <div class="absolute bottom-6 right-6 w-12 h-12 rounded-lg bg-secondary-500/20 flex items-center justify-center text-secondary-400">
                  <i class="fas fa-chalkboard text-xl"></i>
                </div>
              </div>
  
              <!-- Teachers -->
              <div class="bg-surface rounded-xl p-6 shadow-card glass-effect relative overflow-hidden group card-hover">
                <div class="absolute top-0 right-0 w-24 h-24 -mt-8 -mr-8 rounded-full bg-accent-900/20 group-hover:bg-accent-900/30 transition-all"></div>
                <div class="relative">
                  <div class="text-sm text-text-secondary mb-1">Teachers</div>
                  <div class="text-3xl font-bold text-text-primary mb-2">24</div>
                  <div class="flex items-center text-sm text-accent-400">
                    <i class="fas fa-arrow-up mr-1"></i>
                    <span>2 new</span>
                  </div>
                </div>
                <div class="absolute bottom-6 right-6 w-12 h-12 rounded-lg bg-accent-500/20 flex items-center justify-center text-accent-400">
                  <i class="fas fa-chalkboard-teacher text-xl"></i>
                </div>
              </div>
  
              <!-- Students -->
              <div class="bg-surface rounded-xl p-6 shadow-card glass-effect relative overflow-hidden group card-hover">
                <div class="absolute top-0 right-0 w-24 h-24 -mt-8 -mr-8 rounded-full bg-primary-900/20 group-hover:bg-primary-900/30 transition-all"></div>
                <div class="relative">
                  <div class="text-sm text-text-secondary mb-1">Students</div>
                  <div class="text-3xl font-bold text-text-primary mb-2">224</div>
                  <div class="flex items-center text-sm text-accent-400">
                    <i class="fas fa-arrow-up mr-1"></i>
                    <span>10% increase</span>
                  </div>
                </div>
                <div class="absolute bottom-6 right-6 w-12 h-12 rounded-lg bg-primary-500/20 flex items-center justify-center text-primary-400">
                  <i class="fas fa-user-graduate text-xl"></i>
                </div>
              </div>
            </div>
  
            <!-- Recent Activity & Quick Actions -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
              <!-- Recent Activity -->
              <div class="lg:col-span-2 bg-surface rounded-xl shadow-card glass-effect overflow-hidden">
                <div class="px-6 py-4 border-b border-background-light flex justify-between items-center">
                  <h3 class="font-semibold text-text-primary">Recent Activity</h3>
                  <button class="text-text-secondary hover:text-accent-400 transition-colors">
                    <i class="fas fa-ellipsis-h"></i>
                  </button>
                </div>
                <div class="p-0">
                  <div class="divide-y divide-background-light">
                    <div class="flex items-center px-6 py-4 hover:bg-surface-hover transition-colors">
                      <div class="w-10 h-10 rounded-full bg-primary-500/20 flex items-center justify-center mr-4">
                        <i class="fas fa-user-plus text-primary-400"></i>
                      </div>
                      <div class="flex-1">
                        <p class="text-text-primary">New student <span class="font-medium">Fatima Zahra</span> registered</p>
                        <p class="text-xs text-text-secondary">2 hours ago</p>
                      </div>
                    </div>
                    <div class="flex items-center px-6 py-4 hover:bg-surface-hover transition-colors">
                      <div class="w-10 h-10 rounded-full bg-accent-500/20 flex items-center justify-center mr-4">
                        <i class="fas fa-chalkboard text-accent-400"></i>
                      </div>
                      <div class="flex-1">
                        <p class="text-text-primary">New class <span class="font-medium">Web Warriors</span> created</p>
                        <p class="text-xs text-text-secondary">5 hours ago</p>
                      </div>
                    </div>
                    <div class="flex items-center px-6 py-4 hover:bg-surface-hover transition-colors">
                      <div class="w-10 h-10 rounded-full bg-secondary-500/20 flex items-center justify-center mr-4">
                        <i class="fas fa-user-edit text-secondary-400"></i>
                      </div>
                      <div class="flex-1">
                        <p class="text-text-primary">Teacher <span class="font-medium">Said Aabilla</span> profile updated</p>
                        <p class="text-xs text-text-secondary">Yesterday</p>
                      </div>
                    </div>
                    <div class="flex items-center px-6 py-4 hover:bg-surface-hover transition-colors">
                      <div class="w-10 h-10 rounded-full bg-primary-500/20 flex items-center justify-center mr-4">
                        <i class="fas fa-user-plus text-primary-400"></i>
                      </div>
                      <div class="flex-1">
                        <p class="text-text-primary">Students assigned to <span class="font-medium">Aliens</span> class</p>
                        <p class="text-xs text-text-secondary">2 days ago</p>
                      </div>
                    </div>
                    <div class="flex items-center px-6 py-4 hover:bg-surface-hover transition-colors">
                      <div class="w-10 h-10 rounded-full bg-accent-500/20 flex items-center justify-center mr-4">
                        <i class="fas fa-user-edit text-accent-400"></i>
                      </div>
                      <div class="flex-1">
                        <p class="text-text-primary">Student <span class="font-medium">Mohamed Amine</span> profile updated</p>
                        <p class="text-xs text-text-secondary">3 days ago</p>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="px-6 py-3 bg-background-element">
                  <a href="#" class="text-accent-400 hover:text-accent-300 text-sm font-medium">View all activity</a>
                </div>
              </div>
  
              <!-- Quick Actions -->
              <div class="bg-surface rounded-xl shadow-card glass-effect overflow-hidden">
                <div class="px-6 py-4 border-b border-background-light">
                  <h3 class="font-semibold text-text-primary">Quick Actions</h3>
                </div>
                <div class="p-6 space-y-4">
                  <button class="w-full py-3 px-4 bg-primary-600 hover:bg-primary-700 text-white rounded-lg flex items-center justify-center transition-colors">
                    <i class="fas fa-user-plus mr-2"></i>
                    <span>Add New User</span>
                  </button>
                  <button class="w-full py-3 px-4 bg-accent-600 hover:bg-accent-700 text-white rounded-lg flex items-center justify-center transition-colors">
                    <i class="fas fa-plus-circle mr-2"></i>
                    <span>Create Class</span>
                  </button>
                  <button class="w-full py-3 px-4 bg-secondary-600 hover:bg-secondary-700 text-white rounded-lg flex items-center justify-center transition-colors">
                    <i class="fas fa-user-graduate mr-2"></i>
                    <span>Assign Students</span>
                  </button>
                  <button class="w-full py-3 px-4 bg-background-element hover:bg-surface-hover text-text-primary rounded-lg flex items-center justify-center transition-colors">
                    <i class="fas fa-file-export mr-2"></i>
                    <span>Export Reports</span>
                  </button>
                </div>
              </div>
            </div>
          </div>
  
          <!-- Users Section -->
          <div v-if="activeSection === 'users'" class="fade-in">
            <!-- Action Bar -->
            <div class="flex justify-between items-center mb-6">
              <div class="flex space-x-2">
                <button @click="showAddUserModal = true" class="bg-accent-600 hover:bg-accent-700 text-white px-4 py-2 rounded-lg flex items-center transition-colors">
                  <i class="fas fa-plus mr-2"></i>
                  <span>Add User</span>
                </button>
                <button class="bg-background-element hover:bg-surface-hover text-text-primary px-4 py-2 rounded-lg flex items-center transition-colors">
                  <i class="fas fa-filter mr-2"></i>
                  <span>Filter</span>
                </button>
              </div>
              <div class="relative">
                <input 
                  type="text" 
                  placeholder="Search users..." 
                  class="bg-surface border border-background-light rounded-lg px-4 py-2 pl-10 text-text-primary placeholder-text-muted focus:outline-none focus:ring-2 focus:ring-accent-400 w-64"
                >
                <i class="fas fa-search absolute left-3 top-3 text-text-muted"></i>
              </div>
            </div>
  
            <!-- Users Table -->
            <div class="bg-surface rounded-xl shadow-card glass-effect overflow-hidden">
              <div class="px-6 py-4 border-b border-background-light">
                <h3 class="font-semibold text-text-primary">All Users</h3>
              </div>
              <div class="overflow-x-auto">
                <table class="min-w-full divide-y divide-background-light">
                  <thead class="bg-background-element">
                    <tr>
                      <th class="px-6 py-3 text-left text-xs font-medium text-text-secondary uppercase tracking-wider">
                        Name
                      </th>
                      <th class="px-6 py-3 text-left text-xs font-medium text-text-secondary uppercase tracking-wider">
                        Email
                      </th>
                      <th class="px-6 py-3 text-left text-xs font-medium text-text-secondary uppercase tracking-wider">
                        Role
                      </th>
                      <th class="px-6 py-3 text-left text-xs font-medium text-text-secondary uppercase tracking-wider">
                        Class
                      </th>
                      <th class="px-6 py-3 text-left text-xs font-medium text-text-secondary uppercase tracking-wider">
                        Status
                      </th>
                      <th class="px-6 py-3 text-right text-xs font-medium text-text-secondary uppercase tracking-wider">
                        Actions
                      </th>
                    </tr>
                  </thead>
                  <tbody class="divide-y divide-background-light">
                    <!-- Sample users -->
                    <tr class="hover:bg-background-element transition-colors">
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="flex items-center">
                          <div class="h-10 w-10 rounded-full overflow-hidden mr-3">
                            <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="User avatar">
                          </div>
                          <div>
                            <div class="text-sm font-medium text-text-primary">Rida Chaanoun</div>
                            <div class="text-xs text-text-secondary">@ridachaanouni</div>
                          </div>
                        </div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="text-sm text-text-primary">ridachaanouni@youcode.ma</div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <span class="px-2 py-1 text-xs rounded-full font-medium bg-accent-500/20 text-accent-400">
                          Student
                        </span>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-sm text-text-primary">
                        Aliens
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <span class="px-2 py-1 text-xs rounded-full font-medium bg-green-500/20 text-green-500">
                          Active
                        </span>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-right text-sm">
                        <button class="text-accent-400 hover:text-accent-300 mr-3">
                          <i class="fas fa-edit"></i>
                        </button>
                        <button class="text-secondary-400 hover:text-secondary-300">
                          <i class="fas fa-trash-alt"></i>
                        </button>
                      </td>
                    </tr>
                    <tr class="hover:bg-background-element transition-colors">
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="flex items-center">
                          <div class="h-10 w-10 rounded-full overflow-hidden mr-3">
                            <img src="https://randomuser.me/api/portraits/men/22.jpg" alt="User avatar">
                          </div>
                          <div>
                            <div class="text-sm font-medium text-text-primary">Said Aabilla</div>
                            <div class="text-xs text-text-secondary">@saidaabilla</div>
                          </div>
                        </div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="text-sm text-text-primary">saidaabilla@youcode.ma</div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <span class="px-2 py-1 text-xs rounded-full font-medium bg-primary-500/20 text-primary-400">
                          Teacher
                        </span>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-sm text-text-primary">
                        Aliens, Web Warriors
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <span class="px-2 py-1 text-xs rounded-full font-medium bg-green-500/20 text-green-500">
                          Active
                        </span>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-right text-sm">
                        <button class="text-accent-400 hover:text-accent-300 mr-3">
                          <i class="fas fa-edit"></i>
                        </button>
                        <button class="text-secondary-400 hover:text-secondary-300">
                          <i class="fas fa-trash-alt"></i>
                        </button>
                      </td>
                    </tr>
                    <tr class="hover:bg-background-element transition-colors">
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="flex items-center">
                          <div class="h-10 w-10 rounded-full overflow-hidden mr-3">
                            <img src="https://randomuser.me/api/portraits/women/65.jpg" alt="User avatar">
                          </div>
                          <div>
                            <div class="text-sm font-medium text-text-primary">Fatima Zahra</div>
                            <div class="text-xs text-text-secondary">@fatimazahra</div>
                          </div>
                        </div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="text-sm text-text-primary">fatimazahra@youcode.ma</div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <span class="px-2 py-1 text-xs rounded-full font-medium bg-accent-500/20 text-accent-400">
                          Student
                        </span>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-sm text-text-primary">
                        Aliens
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <span class="px-2 py-1 text-xs rounded-full font-medium bg-green-500/20 text-green-500">
                          Active
                        </span>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-right text-sm">
                        <button class="text-accent-400 hover:text-accent-300 mr-3">
                          <i class="fas fa-edit"></i>
                        </button>
                        <button class="text-secondary-400 hover:text-secondary-300">
                          <i class="fas fa-trash-alt"></i>
                        </button>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
              <!-- Pagination -->
              <div class="px-6 py-3 flex items-center justify-between border-t border-background-light">
                <div class="text-sm text-text-secondary">
                  Showing <span class="font-medium">1</span> to <span class="font-medium">10</span> of <span class="font-medium">248</span> results
                </div>
                <div class="flex space-x-1">
                  <button class="px-3 py-1 rounded-md bg-background-element text-text-secondary hover:bg-surface-hover transition-colors">
                    Previous
                  </button>
                  <button class="px-3 py-1 rounded-md bg-accent-600 text-white">
                    1
                  </button>
                  <button class="px-3 py-1 rounded-md bg-background-element text-text-secondary hover:bg-surface-hover transition-colors">
                    2
                  </button>
                  <button class="px-3 py-1 rounded-md bg-background-element text-text-secondary hover:bg-surface-hover transition-colors">
                    3
                  </button>
                  <button class="px-3 py-1 rounded-md bg-background-element text-text-secondary hover:bg-surface-hover transition-colors">
                    Next
                  </button>
                </div>
              </div>
            </div>
          </div>
  
          <!-- Classes Section -->
          <div v-if="activeSection === 'classes'" class="fade-in">
            <!-- Action Bar -->
            <div class="flex justify-between items-center mb-6">
              <div class="flex space-x-2">
                <button @click="showAddClassModal = true" class="bg-accent-600 hover:bg-accent-700 text-white px-4 py-2 rounded-lg flex items-center transition-colors">
                  <i class="fas fa-plus mr-2"></i>
                  <span>Add Class</span>
                </button>
                <button class="bg-background-element hover:bg-surface-hover text-text-primary px-4 py-2 rounded-lg flex items-center transition-colors">
                  <i class="fas fa-filter mr-2"></i>
                  <span>Filter</span>
                </button>
              </div>
              <div class="relative">
                <input 
                  type="text" 
                  placeholder="Search classes..." 
                  class="bg-surface border border-background-light rounded-lg px-4 py-2 pl-10 text-text-primary placeholder-text-muted focus:outline-none focus:ring-2 focus:ring-accent-400 w-64"
                >
                <i class="fas fa-search absolute left-3 top-3 text-text-muted"></i>
              </div>
            </div>
  
            <!-- Classes Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
              <!-- Class Card 1 -->
              <div class="bg-surface rounded-xl shadow-card glass-effect overflow-hidden card-hover">
                <!-- Class Header -->
                <div class="h-32 bg-gradient-to-r from-primary-700 to-primary-500 relative p-6">
                  <h3 class="font-bold text-xl text-white mb-1">Aliens</h3>
                  <p class="text-primary-100">1ère Année</p>
                  <div class="absolute top-4 right-4 bg-white/20 rounded-full p-2">
                    <i class="fas fa-laptop-code text-white"></i>
                  </div>
                </div>
                
                <!-- Class Details -->
                <div class="p-6">
                  <div class="space-y-4">
                    <!-- Teacher -->
                    <div class="flex items-center justify-between">
                      <div class="flex items-center">
                        <div class="w-8 h-8 rounded-full flex items-center justify-center bg-primary-500/20 mr-3">
                          <i class="fas fa-chalkboard-teacher text-primary-400 text-sm"></i>
                        </div>
                        <span class="text-text-secondary text-sm">Teacher</span>
                      </div>
                      <span class="font-medium text-text-primary">Said Aabilla</span>
                    </div>
                    
                    <!-- Students -->
                    <div class="flex items-center justify-between">
                      <div class="flex items-center">
                        <div class="w-8 h-8 rounded-full flex items-center justify-center bg-accent-500/20 mr-3">
                          <i class="fas fa-users text-accent-400 text-sm"></i>
                        </div>
                        <span class="text-text-secondary text-sm">Students</span>
                      </div>
                      <span class="font-medium text-text-primary">22</span>
                    </div>
                    
                                    <!-- Campus -->
                                    <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-secondary-500/20 mr-3">
                        <i class="fas fa-building text-secondary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Campus</span>
                    </div>
                    <span class="font-medium text-text-primary">Youssoufia</span>
                  </div>

                  <!-- Promotion -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-primary-500/20 mr-3">
                        <i class="fas fa-calendar-day text-primary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Promotion</span>
                    </div>
                    <span class="font-medium text-text-primary">2024-2025</span>
                  </div>
                </div>
              </div>
              
              <!-- Actions -->
              <div class="border-t border-background-light p-4 bg-background-element flex justify-between">
                <button class="text-accent-400 hover:text-accent-300 flex items-center text-sm">
                  <i class="fas fa-edit mr-1"></i>
                  <span>Edit</span>
                </button>
                <button class="text-accent-400 hover:text-accent-300 flex items-center text-sm">
                  <i class="fas fa-users mr-1"></i>
                  <span>Manage Students</span>
                </button>
              </div>
            </div>

            <!-- Class Card 2 -->
            <div class="bg-surface rounded-xl shadow-card glass-effect overflow-hidden card-hover">
              <!-- Class Header -->
              <div class="h-32 bg-gradient-to-r from-accent-700 to-accent-500 relative p-6">
                <h3 class="font-bold text-xl text-white mb-1">Web Warriors</h3>
                <p class="text-accent-100">2ème Année</p>
                <div class="absolute top-4 right-4 bg-white/20 rounded-full p-2">
                  <i class="fas fa-code text-white"></i>
                </div>
              </div>
              
              <!-- Class Details -->
              <div class="p-6">
                <div class="space-y-4">
                  <!-- Teacher -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-primary-500/20 mr-3">
                        <i class="fas fa-chalkboard-teacher text-primary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Teacher</span>
                    </div>
                    <span class="font-medium text-text-primary">Abdelhafid Belfqir</span>
                  </div>
                  
                  <!-- Students -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-accent-500/20 mr-3">
                        <i class="fas fa-users text-accent-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Students</span>
                    </div>
                    <span class="font-medium text-text-primary">18</span>
                  </div>
                  
                  <!-- Campus -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-secondary-500/20 mr-3">
                        <i class="fas fa-building text-secondary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Campus</span>
                    </div>
                    <span class="font-medium text-text-primary">Youssoufia</span>
                  </div>

                  <!-- Promotion -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-primary-500/20 mr-3">
                        <i class="fas fa-calendar-day text-primary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Promotion</span>
                    </div>
                    <span class="font-medium text-text-primary">2024-2025</span>
                  </div>
                </div>
              </div>
              
              <!-- Actions -->
              <div class="border-t border-background-light p-4 bg-background-element flex justify-between">
                <button class="text-accent-400 hover:text-accent-300 flex items-center text-sm">
                  <i class="fas fa-edit mr-1"></i>
                  <span>Edit</span>
                </button>
                <button class="text-accent-400 hover:text-accent-300 flex items-center text-sm">
                  <i class="fas fa-users mr-1"></i>
                  <span>Manage Students</span>
                </button>
              </div>
            </div>

            <!-- Class Card 3 -->
            <div class="bg-surface rounded-xl shadow-card glass-effect overflow-hidden card-hover">
              <!-- Class Header -->
              <div class="h-32 bg-gradient-to-r from-secondary-700 to-secondary-500 relative p-6">
                <h3 class="font-bold text-xl text-white mb-1">Data Masters</h3>
                <p class="text-secondary-100">2ème Année</p>
                <div class="absolute top-4 right-4 bg-white/20 rounded-full p-2">
                  <i class="fas fa-database text-white"></i>
                </div>
              </div>
              
              <!-- Class Details -->
              <div class="p-6">
                <div class="space-y-4">
                  <!-- Teacher -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-primary-500/20 mr-3">
                        <i class="fas fa-chalkboard-teacher text-primary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Teacher</span>
                    </div>
                    <span class="font-medium text-text-primary">Sarah Moukrim</span>
                  </div>
                  
                  <!-- Students -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-accent-500/20 mr-3">
                        <i class="fas fa-users text-accent-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Students</span>
                    </div>
                    <span class="font-medium text-text-primary">20</span>
                  </div>
                  
                  <!-- Campus -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-secondary-500/20 mr-3">
                        <i class="fas fa-building text-secondary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Campus</span>
                    </div>
                    <span class="font-medium text-text-primary">Youssoufia</span>
                  </div>

                  <!-- Promotion -->
                  <div class="flex items-center justify-between">
                    <div class="flex items-center">
                      <div class="w-8 h-8 rounded-full flex items-center justify-center bg-primary-500/20 mr-3">
                        <i class="fas fa-calendar-day text-primary-400 text-sm"></i>
                      </div>
                      <span class="text-text-secondary text-sm">Promotion</span>
                    </div>
                    <span class="font-medium text-text-primary">2024-2025</span>
                  </div>
                </div>
              </div>
              
              <!-- Actions -->
              <div class="border-t border-background-light p-4 bg-background-element flex justify-between">
                <button class="text-accent-400 hover:text-accent-300 flex items-center text-sm">
                  <i class="fas fa-edit mr-1"></i>
                  <span>Edit</span>
                </button>
                <button class="text-accent-400 hover:text-accent-300 flex items-center text-sm">
                  <i class="fas fa-users mr-1"></i>
                  <span>Manage Students</span>
                </button>
              </div>
            </div>
          </div>
          
          <!-- Pagination for classes -->
          <div class="mt-6 flex justify-center">
            <div class="flex space-x-1">
              <button class="px-3 py-1 rounded-md bg-background-element text-text-secondary hover:bg-surface-hover transition-colors">
                Previous
              </button>
              <button class="px-3 py-1 rounded-md bg-accent-600 text-white">
                1
              </button>
              <button class="px-3 py-1 rounded-md bg-background-element text-text-secondary hover:bg-surface-hover transition-colors">
                2
              </button>
              <button class="px-3 py-1 rounded-md bg-background-element text-text-secondary hover:bg-surface-hover transition-colors">
                Next
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Add User Modal -->
    <div v-if="showAddUserModal" class="fixed inset-0 flex items-center justify-center z-50">
      <!-- Overlay -->
      <div class="absolute inset-0 bg-black/70" @click="showAddUserModal = false"></div>
      
      <!-- Modal Content -->
      <div class="relative bg-surface rounded-xl shadow-lg glass-effect w-full max-w-md mx-4 p-6 fade-in">
        <div class="flex justify-between items-center mb-6">
          <h3 class="text-xl font-bold text-text-primary">Add New User</h3>
          <button @click="showAddUserModal = false" class="text-text-secondary hover:text-accent-400 transition-colors">
            <i class="fas fa-times"></i>
          </button>
        </div>
        
        <form @submit.prevent="addUser">
          <div class="space-y-4">
            <!-- First Name & Last Name -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-medium text-text-secondary mb-1">First Name</label>
                <input 
                  v-model="newUser.firstName"
                  type="text" 
                  class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                  required
                >
              </div>
              <div>
                <label class="block text-sm font-medium text-text-secondary mb-1">Last Name</label>
                <input 
                  v-model="newUser.lastName"
                  type="text" 
                  class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                  required
                >
              </div>
            </div>
            
            <!-- Email -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Email</label>
              <input 
                v-model="newUser.email"
                type="email" 
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
            </div>
            
            <!-- Username -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Username</label>
              <div class="relative">
                <span class="absolute inset-y-0 left-0 pl-3 flex items-center text-text-muted">@</span>
                <input 
                  v-model="newUser.username"
                  type="text" 
                  class="w-full bg-background-element border border-background-light rounded-lg pl-8 pr-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                  required
                >
              </div>
            </div>
            
            <!-- Role -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Role</label>
              <select 
                v-model="newUser.role"
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
                <option value="">Select a role</option>
                <option value="student">Student</option>
                <option value="teacher">Teacher</option>
                <option value="admin">Admin</option>
              </select>
            </div>
            
            <!-- Class (if student) -->
            <div v-if="newUser.role === 'student'">
              <label class="block text-sm font-medium text-text-secondary mb-1">Class</label>
              <select 
                v-model="newUser.class"
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
                <option value="">Select a class</option>
                <option value="Aliens">Aliens</option>
                <option value="Web Warriors">Web Warriors</option>
                <option value="Data Masters">Data Masters</option>
              </select>
            </div>
            
            <!-- Password -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Password</label>
              <input 
                v-model="newUser.password"
                type="password" 
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
            </div>
            
            <!-- Confirm Password -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Confirm Password</label>
              <input 
                v-model="newUser.confirmPassword"
                type="password" 
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
            </div>
          </div>
          
          <div class="mt-6 flex justify-end space-x-3">
            <button 
              type="button"
              @click="showAddUserModal = false"
              class="px-4 py-2 rounded-lg border border-background-light text-text-primary hover:bg-background-element transition-colors"
            >
              Cancel
            </button>
            <button 
              type="submit"
              class="px-4 py-2 rounded-lg bg-accent-600 hover:bg-accent-700 text-white transition-colors"
            >
              Add User
            </button>
          </div>
        </form>
      </div>
    </div>
    
    <!-- Add Class Modal -->
    <div v-if="showAddClassModal" class="fixed inset-0 flex items-center justify-center z-50">
      <!-- Overlay -->
      <div class="absolute inset-0 bg-black/70" @click="showAddClassModal = false"></div>
      
      <!-- Modal Content -->
      <div class="relative bg-surface rounded-xl shadow-lg glass-effect w-full max-w-md mx-4 p-6 fade-in">
        <div class="flex justify-between items-center mb-6">
          <h3 class="text-xl font-bold text-text-primary">Add New Class</h3>
          <button @click="showAddClassModal = false" class="text-text-secondary hover:text-accent-400 transition-colors">
            <i class="fas fa-times"></i>
          </button>
        </div>
        
        <form @submit.prevent="addClass">
          <div class="space-y-4">
            <!-- Class Name -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Class Name</label>
              <input 
                v-model="newClass.name"
                type="text" 
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
            </div>
            
            <!-- Level -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Level</label>
              <select 
                v-model="newClass.level"
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
                <option value="">Select a level</option>
                <option value="1ère Année">1ère Année</option>
                <option value="2ème Année">2ème Année</option>
              </select>
            </div>
            
            <!-- Teacher -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Teacher</label>
              <select 
                v-model="newClass.teacher"
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
                <option value="">Select a teacher</option>
                <option value="Said Aabilla">Said Aabilla</option>
                <option value="Sarah Moukrim">Sarah Moukrim</option>
                <option value="Abdelhafid Belfqir">Abdelhafid Belfqir</option>
              </select>
            </div>
            
            <!-- Campus -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Campus</label>
              <select 
                v-model="newClass.campus"
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
                <option value="">Select a campus</option>
                <option value="Youssoufia">Youssoufia</option>
                <option value="Safi">Safi</option>
              </select>
            </div>
            
            <!-- Promotion -->
            <div>
              <label class="block text-sm font-medium text-text-secondary mb-1">Promotion</label>
              <input 
                v-model="newClass.promotion"
                type="text" 
                placeholder="e.g. 2024-2025"
                class="w-full bg-background-element border border-background-light rounded-lg px-4 py-2.5 text-text-primary focus:outline-none focus:ring-2 focus:ring-accent-400"
                required
              >
            </div>
          </div>
          
          <div class="mt-6 flex justify-end space-x-3">
            <button 
              type="button"
              @click="showAddClassModal = false"
              class="px-4 py-2 rounded-lg border border-background-light text-text-primary hover:bg-background-element transition-colors"
            >
              Cancel
            </button>
            <button 
              type="submit"
              class="px-4 py-2 rounded-lg bg-accent-600 hover:bg-accent-700 text-white transition-colors"
            >
              Add Class
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  name: 'AdminDashboard',
  setup() {
    // Active section state
    const activeSection = ref('dashboard');
    
    // Modal states
    const showAddUserModal = ref(false);
    const showAddClassModal = ref(false);

    // Current date and time
    const currentDateTime = ref('2025-03-12 14:01:01');
    
    // User form data
    const newUser = ref({
      firstName: '',
      lastName: '',
      email: '',
      username: '',
      role: '',
      class: '',
      password: '',
      confirmPassword: ''
    });
    
    // Class form data
    const newClass = ref({
      name: '',
      level: '',
      teacher: '',
      campus: '',
      promotion: ''
    });
    
    // Computed properties
    const sectionTitle = computed(() => {
      switch(activeSection.value) {
        case 'dashboard': return 'Admin Dashboard';
        case 'users': return 'User Management';
        case 'classes': return 'Class Management';
        default: return 'Admin Dashboard';
      }
    });
    
    // Methods
    const addUser = () => {
      // Form validation
      if(newUser.value.password !== newUser.value.confirmPassword) {
        alert('Passwords do not match!');
        return;
      }
      
      // In a real application, you would send this data to an API
      console.log('Adding new user:', newUser.value);
      
      // Reset form and close modal
      newUser.value = {
        firstName: '',
        lastName: '',
        email: '',
        username: '',
        role: '',
        class: '',
        password: '',
        confirmPassword: ''
      };
      
      showAddUserModal.value = false;
      
      // Show success notification
      alert('User added successfully!');
    };
    
    const addClass = () => {
      // In a real application, you would send this data to an API
      console.log('Adding new class:', newClass.value);
      
      // Reset form and close modal
      newClass.value = {
        name: '',
        level: '',
        teacher: '',
        campus: '',
        promotion: ''
      };
      
      showAddClassModal.value = false;
      
      // Show success notification
      alert('Class added successfully!');
    };
    
    
    return {
      activeSection,
      currentDateTime,
      showAddUserModal,
      showAddClassModal,
      newUser,
      newClass,
      sectionTitle,
      addUser,
      addClass
    };
  }
};
</script>

<style scoped>
/* Fade in animation */
.fade-in {
  animation: fadeIn 0.3s ease-in-out;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Card hover */
.card-hover {
  transition: all 0.3s ease;
}

.card-hover:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 20px -5px rgba(0, 0, 0, 0.5);
}
</style>  