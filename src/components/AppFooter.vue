<template>
  <v-footer
    app
    height="80"
    class="custom-footer"
  >
    <div class="social-container">
      <a
        v-for="item in items"
        :key="item.title"
        class="social-link"
        :href="item.href"
        rel="noopener noreferrer"
        target="_blank"
        :title="item.title"
      >
        <v-icon
          :icon="item.icon"
          size="24"
          class="social-icon"
        />
      </a>
    </div>

    <div class="footer-info">
      <span class="copyright">
        &copy; 2016-{{ (new Date()).getFullYear() }} 
        <span class="institution-name">Institución Educativa Comfacor</span>
      </span>
      <span class="separator">—</span>
      <a
        class="policy-link"
        href="#"
        rel="noopener noreferrer"
        target="_blank"
      >
        Políticas de Privacidad
      </a>
    </div>
  </v-footer>
</template>

<script setup>
  const items = [
    {
      title: 'Facebook',
      icon: 'mdi-facebook',
      href: '#',
    },
    {
      title: 'Instagram',
      icon: 'mdi-instagram',
      href: '#',
    },
    {
      title: 'Twitter',
      icon: 'mdi-twitter',
      href: '#',
    },
    {
      title: 'YouTube',
      icon: 'mdi-youtube',
      href: '#',
    },
    {
      title: 'Email',
      icon: 'mdi-email',
      href: '#',
    },
  ]
</script>

<style scoped lang="sass">
.custom-footer
  background: linear-gradient(135deg, #e3f2fd 0%, #f5fbff 100%) !important
  border-top: 3px solid #b3e5fc !important
  box-shadow: 0 -4px 20px rgba(179, 229, 252, 0.4) !important
  display: flex
  align-items: center
  justify-content: space-between
  padding: 0 24px !important
  position: relative
  overflow: hidden

.custom-footer::before
  content: ''
  position: absolute
  top: 0
  left: 0
  right: 0
  height: 2px
  background: linear-gradient(90deg, #4FC3F7, #0288D1, #4FC3F7)
  animation: shimmer 3s ease-in-out infinite

@keyframes shimmer
  0%, 100%
    opacity: 0.7
  50%
    opacity: 1

.social-container
  display: flex
  gap: 8px
  align-items: center

.social-link
  display: flex
  align-items: center
  justify-content: center
  width: 44px
  height: 44px
  border-radius: 50%
  background: linear-gradient(135deg, #FFFFFF 0%, #F5FBFF 100%)
  border: 2px solid #B3E5FC
  box-shadow: 0 4px 12px rgba(179, 229, 252, 0.3)
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94)
  position: relative
  overflow: hidden
  text-decoration: none

.social-link::before
  content: ''
  position: absolute
  top: 0
  left: -100%
  width: 100%
  height: 100%
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.6), transparent)
  transition: left 0.5s ease

.social-link:hover::before
  left: 100%

.social-link:hover
  background: linear-gradient(135deg, #4FC3F7 0%, #0288D1 100%)
  border-color: #0288D1
  transform: translateY(-3px) scale(1.1)
  box-shadow: 0 8px 20px rgba(2, 136, 209, 0.4)

.social-icon
  color: #0277BD !important
  transition: all 0.4s ease !important
  font-size: 20px

.social-link:hover .social-icon
  color: #FFFFFF !important
  transform: scale(1.1)

.footer-info
  display: flex
  align-items: center
  gap: 12px
  color: #01579B
  font-size: 0.875rem
  font-weight: 500

.copyright
  display: flex
  align-items: center
  gap: 4px

.institution-name
  font-weight: 600
  color: #01579B

.separator
  color: #0277BD

.policy-link
  color: #0277BD !important
  text-decoration: none
  font-weight: 500
  transition: all 0.3s ease
  position: relative
  padding: 4px 8px
  border-radius: 6px

.policy-link::after
  content: ''
  position: absolute
  bottom: 0
  left: 50%
  width: 0
  height: 2px
  background: linear-gradient(90deg, #4FC3F7, #0288D1)
  transition: all 0.3s ease
  transform: translateX(-50%)

.policy-link:hover
  color: #01579B !important
  background: rgba(179, 229, 252, 0.2)

.policy-link:hover::after
  width: 100%

/* Responsive */
@media (max-width: 960px)
  .custom-footer
    flex-direction: column
    gap: 16px
    padding: 16px !important
    height: auto !important
    min-height: 80px

  .footer-info
    flex-direction: column
    gap: 8px
    text-align: center

  .separator
    display: none

@media (max-width: 600px)
  .social-container
    gap: 6px

  .social-link
    width: 40px
    height: 40px

  .social-icon
    font-size: 18px !important

  .footer-info
    font-size: 0.8rem
    gap: 6px

  .institution-name
    display: block
    text-align: center

@media (max-width: 400px)
  .social-link
    width: 36px
    height: 36px

  .social-icon
    font-size: 16px !important

  .footer-info
    font-size: 0.75rem

  .policy-link
    padding: 2px 6px
</style>