# Pass for a PWA in an existing project
 
 1. yarn add -D vite-plugin-pwa

 2. En el archivo vite.config.mts en el array en plugins agregar e importar:

 import { VitePWA } from 'vite-plugin-pwa'

 VitePWA({
      registerType: 'prompt',
      injectRegister: false,

      pwaAssets: {
        disabled: false,
        config: true,
      },

      manifest: {
        name: 'vuetify-pwa',
        short_name: 'vuefy-pwa',
        description: 'vuetify-pwa-test',
        theme_color: '#ffffff',
      },

      workbox: {
        globPatterns: ['**/*.{js,css,html,svg,png,ico}'],
        cleanupOutdatedCaches: true,
        clientsClaim: true,
      },

      devOptions: {
        enabled: false,
        navigateFallback: 'index.html',
        suppressWarnings: true,
        type: 'module',
      },
    }),


 3. En public agregar un favicon.svg (Logo)

 4. crear en la raiz del proyecto el archivo "pwa-assets.config.ts" y pegar este código:

  import {
      defineConfig,
      minimal2023Preset as preset,
  } from '@vite-pwa/assets-generator/config'

  export default defineConfig({
      headLinkOptions: {
          preset: '2023',
      },
      preset,
      images: ['public/favicon.svg'],
  })


 5. yarn add -D @vite-pwa/assets-generator

 6. Agregar en el object scripts de package.json:
 
    {
        "scripts": {
            "generate-pwa-assets": "pwa-assets-generator"
        }
    }

 7. Agregar en package.json este object:

  "resolutions": {
    "sharp": "0.32.6",
    "sharp-ico": "0.1.5"
  }

 8. yarn generate-pwa-assets

 

  #Update form branch icon-test
