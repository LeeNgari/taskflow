<template>
  <header class="w-full bg-white border-b shadow-sm fixed top-0 left-0 z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3 flex items-center justify-between">
      
      <!-- Left: Logo + Title -->
      <div class="flex items-center gap-3">
        <img
          src="https://res.cloudinary.com/du74ofrgc/image/upload/v1752508081/Screenshot_from_2025-07-14_15-16-08_qlidps.png"
          alt="TaskFlow Logo"
          class="w-10 h-10 object-contain rounded-md"
        />
        <div>
          <h1 class="text-xl font-semibold text-gray-900">TaskFlow</h1>
          <p class="text-sm text-gray-500">Admin Dashboard</p>
        </div>
      </div>

      <!-- Right: Logout Button -->
      <Button 
        @click="logout" 
        variant="ghost" 
        class="hover:bg-blue-50 gap-2 px-4 py-2 text-gray-700 font-medium"
      >
        <LogOut class="h-4 w-4" />
        Logout
      </Button>
    </div>
  </header>

  <!-- Spacer to offset fixed header -->
  <div class="h-[72px]"></div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { useAuthStore } from '@/stores/auth'
import {
  ClipboardList,
  LogOut,
} from 'lucide-vue-next'
import { Button } from '@/components/ui/button'
import { Card, CardHeader, CardTitle } from '@/components/ui/card'

const authStore = useAuthStore()
const router = useRouter()

const logout = async () => {
  await authStore.logout();
  router.push('/login');
};
</script>
