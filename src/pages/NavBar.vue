<template>
  <div style="min-height: 100vh; background: linear-gradient(to bottom right, #f8fafc, #ffffff, #f1f5f9); display: flex; align-items: center; justify-content: center; padding: 1rem; position: relative;">

    <!-- Header -->
    <div style="position: absolute; top: 0; left: 0; right: 0; padding: 2rem; text-align: center;">
      <h1 style="font-size: 2.25rem; font-weight: 300; color: #0f172a; margin: 0 0 0.5rem 0; letter-spacing: -0.02em;">
        Hover <span style="background: linear-gradient(to right, #b45309, #a4161a); -webkit-background-clip: text; -webkit-text-fill-color: transparent; font-weight: 600;">Refinado</span>
      </h1>
      <p style="color: #64748b; font-size: 1rem; font-weight: 300; margin: 0;">Hover nos ícones</p>
    </div>

    <!-- Icons Container -->
    <div style="display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; max-width: 600px;">
      <div
        v-for="item in icons"
        :key="item.id"
        :style="{
          position: 'relative',
          width: '100px',
          height: '100px',
          cursor: 'pointer',
          flexShrink: 0,
        }"
        @mouseenter="hoveredIcon = item.id"
        @mouseleave="hoveredIcon = null"
      >
        <!-- Glow -->
        <div
          :style="{
            position: 'absolute',
            inset: 0,
            borderRadius: '1rem',
            filter: 'blur(24px)',
            background: item.glowColor,
            opacity: hoveredIcon === item.id ? 1 : 0,
            transform: hoveredIcon === item.id ? 'scale(1.1)' : 'scale(0.95)',
            transition: 'all 0.7s ease',
            zIndex: 0,
          }"
        />

        <!-- Card -->
        <div
          :style="{
            position: 'relative',
            width: '100%',
            height: '100%',
            backgroundColor: '#ffffff',
            borderRadius: '1rem',
            border: '1px solid #e2e8f0',
            display: 'flex',
            flexDirection: 'column',
            alignItems: 'center',
            justifyContent: 'center',
            padding: '1rem',
            transition: 'all 0.7s ease',
            boxShadow: hoveredIcon === item.id ? '0 20px 25px -5px rgba(0, 0, 0, 0.1)' : '0 10px 15px -3px rgba(0, 0, 0, 0.1)',
            transform: hoveredIcon === item.id ? 'translateY(-8px)' : 'translateY(0)',
            borderColor: hoveredIcon === item.id ? '#cbd5e1' : '#e2e8f0',
            zIndex: 1,
          }"
        >
          <!-- Icon Container -->
          <div
            :style="{
              width: '56px',
              height: '56px',
              borderRadius: '0.75rem',
              background: item.color,
              display: 'flex',
              alignItems: 'center',
              justifyContent: 'center',
              transition: 'all 0.7s ease',
              transform: hoveredIcon === item.id ? 'scale(1.1)' : 'scale(1)',
              boxShadow: hoveredIcon === item.id ? '0 10px 15px -3px rgba(0, 0, 0, 0.1)' : '0 4px 6px -1px rgba(0, 0, 0, 0.1)',
            }"
          >
            <!-- SVG Icons -->
            <svg
              v-if="item.id === 1"
              fill="none"
              stroke="currentColor"
              :style="{
                width: '28px',
                height: '28px',
                color: 'white',
                strokeWidth: '1.5px',
                transition: 'all 0.7s ease',
                transform: hoveredIcon === item.id ? 'scale(1.1)' : 'scale(1)',
              }"
              viewBox="0 0 24 24"
            >
              <path d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-9-5a4 4 0 100 8 4 4 0 000-8z" stroke-linecap="round" stroke-linejoin="round" />
            </svg>

            <svg
              v-if="item.id === 2"
              fill="none"
              stroke="currentColor"
              :style="{
                width: '28px',
                height: '28px',
                color: 'white',
                strokeWidth: '1.5px',
                transition: 'all 0.7s ease',
                transform: hoveredIcon === item.id ? 'scale(1.1)' : 'scale(1)',
              }"
              viewBox="0 0 24 24"
            >
              <path d="M10 20l4-16m4 4l4 4m0 0l-4 4m4-4H3" stroke-linecap="round" stroke-linejoin="round" />
            </svg>

            <svg
              v-if="item.id === 3"
              fill="none"
              stroke="currentColor"
              :style="{
                width: '28px',
                height: '28px',
                color: 'white',
                strokeWidth: '1.5px',
                transition: 'all 0.7s ease',
                transform: hoveredIcon === item.id ? 'scale(1.1)' : 'scale(1)',
              }"
              viewBox="0 0 24 24"
            >
              <path d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.5a2 2 0 00-1 .267M7 21H5a2 2 0 01-2-2v-4a2 2 0 012-2h2.5" stroke-linecap="round" stroke-linejoin="round" />
            </svg>

            <svg
              v-if="item.id === 4"
              fill="none"
              stroke="currentColor"
              :style="{
                width: '28px',
                height: '28px',
                color: 'white',
                strokeWidth: '1.5px',
                transition: 'all 0.7s ease',
                transform: hoveredIcon === item.id ? 'scale(1.1)' : 'scale(1)',
              }"
              viewBox="0 0 24 24"
            >
              <path d="M13 10V3L4 14h7v7l9-11h-7z" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </div>

          <!-- Bottom line -->
          <div
            :style="{
              position: 'absolute',
              bottom: '4px',
              left: '50%',
              transform: 'translateX(-50%)',
              height: '2px',
              background: item.color,
              borderRadius: '9999px',
              transition: 'all 0.7s ease',
              width: hoveredIcon === item.id ? '16px' : '8px',
              opacity: hoveredIcon === item.id ? 1 : 0.3,
            }"
          />

          <!-- Label on hover -->
          <div
            v-if="hoveredIcon === item.id"
            :style="{
              position: 'absolute',
              bottom: '-32px',
              left: '50%',
              transform: 'translateX(-50%)',
              fontSize: '0.75rem',
              fontWeight: '500',
              color: '#475569',
              whiteSpace: 'nowrap',
              animation: 'fadeIn 0.3s ease-in-out',
            }"
          >
            {{ item.label }}
          </div>
        </div>
      </div>
    </div>

    <!-- Bottom text -->
    <div style="position: absolute; bottom: 2rem; left: 0; right: 0; text-align: center;">
      <p style="color: #9ca3af; font-size: 0.875rem; font-weight: 300; letter-spacing: 0.1em; margin: 0;">
        Mobile friendly • Hover para ver efeito
      </p>
    </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue'

  const hoveredIcon = ref(null)

  const icons = [
    {
      id: 1,
      label: 'Design',
      color: 'linear-gradient(to bottom right, #fcd34d, #fef3c7)',
      glowColor: 'rgba(217, 119, 6, 0.2)',
    },
    {
      id: 2,
      label: 'Dev',
      color: 'linear-gradient(to bottom right, #cbd5e1, #e5e7eb)',
      glowColor: 'rgba(71, 85, 105, 0.2)',
    },
    {
      id: 3,
      label: 'Creative',
      color: 'linear-gradient(to bottom right, #fda4af, #fce7f3)',
      glowColor: 'rgba(190, 24, 93, 0.2)',
    },
    {
      id: 4,
      label: 'Perf',
      color: 'linear-gradient(to bottom right, #67e8f9, #bfdbfe)',
      glowColor: 'rgba(6, 182, 212, 0.2)',
    },
  ]
</script>

<style scoped>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-4px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
