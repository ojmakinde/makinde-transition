<template>
  <div class="policy-section" :class="{ expanded: isExpanded }">
    <button 
      class="policy-header"
      @click="toggleExpanded"
      :aria-expanded="isExpanded"
    >
      <div class="policy-header-content">
        <h4 class="policy-title">{{ section.title }}</h4>
        <p class="policy-subtitle">{{ section.subtitle }}</p>
      </div>
      <span class="policy-toggle" aria-hidden="true">
        <svg v-if="!isExpanded" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <line x1="12" y1="5" x2="12" y2="19"></line>
          <line x1="5" y1="12" x2="19" y2="12"></line>
        </svg>
        <svg v-else width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <line x1="5" y1="12" x2="19" y2="12"></line>
        </svg>
      </span>
    </button>
    
    <div class="policy-content" v-show="isExpanded">
      <div class="policy-details">
        <div class="policy-item">
          <h5 class="policy-item-title">The Problem</h5>
          <p class="policy-item-text">{{ section.content.problem }}</p>
        </div>
        
        <div class="policy-item">
          <h5 class="policy-item-title">The Solution</h5>
          <p class="policy-item-text">{{ section.content.solution }}</p>
        </div>
        
        <div class="policy-item">
          <h5 class="policy-item-title">The Impact</h5>
          <p class="policy-item-text">{{ section.content.impact }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PolicySection',
  props: {
    section: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      isExpanded: false
    }
  },
  methods: {
    toggleExpanded() {
      this.isExpanded = !this.isExpanded
    }
  }
}
</script>

<style scoped>
.policy-section {
  border-bottom: 1px solid var(--border-color);
  transition: var(--transition);
}

.policy-section:first-child {
  border-top: 1px solid var(--border-color);
}

.policy-header {
  width: 100%;
  padding: 40px 0;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: transparent;
  border: none;
  text-align: left;
  transition: var(--transition);
  font-family: inherit;
}

.policy-header:hover {
  opacity: 0.8;
}

.policy-header:focus {
  outline: none;
}

.policy-header:focus-visible {
  outline: 2px solid var(--accent-color);
  outline-offset: 4px;
}

.policy-header-content {
  flex: 1;
  padding-right: 24px;
}

.policy-title {
  font-size: clamp(1.75rem, 4vw, 2.5rem);
  font-weight: 700;
  margin: 0 0 8px 0;
  letter-spacing: -0.02em;
  line-height: 1.2;
  color: var(--primary-color);
}

.policy-subtitle {
  font-size: 1.1rem;
  color: var(--text-light);
  margin: 0;
  line-height: 1.4;
}

.policy-toggle {
  flex-shrink: 0;
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: var(--bg-light);
  color: var(--primary-color);
  transition: var(--transition);
}

.policy-header:hover .policy-toggle {
  background: var(--primary-color);
  color: white;
}

.policy-section.expanded .policy-toggle {
  background: var(--primary-color);
  color: white;
}

.policy-content {
  padding: 0 0 60px 0;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.policy-details {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 40px;
  background: var(--bg-light);
  padding: 48px;
  border-radius: 12px;
}

.policy-item {
  padding: 0;
}

.policy-item-title {
  font-size: 0.875rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 16px;
  color: var(--accent-color);
}

.policy-item-text {
  font-size: 1.05rem;
  line-height: 1.7;
  color: var(--text-color);
  margin: 0;
}

@media (max-width: 768px) {
  .policy-header {
    padding: 32px 0;
  }

  .policy-toggle {
    width: 40px;
    height: 40px;
  }

  .policy-toggle svg {
    width: 20px;
    height: 20px;
  }

  .policy-content {
    padding: 0 0 40px 0;
  }

  .policy-details {
    padding: 32px 24px;
    gap: 32px;
  }

  .policy-item-text {
    font-size: 1rem;
  }
}
</style>
