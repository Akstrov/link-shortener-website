<script setup>
import InputText from 'primevue/inputtext'
import Card from 'primevue/card'
import Button from 'primevue/button'
import axios from 'axios'
</script>

<template>
  <main>
    <Card>
      <template #title> Shorten URL </template>
      <template #content>
        <div style="margin: 1rem">
          <span class="p-input-icon-left">
            <i class="pi pi-search" />
            <InputText placeholder="Search" v-model="url" />
          </span>
          <Button style="margin-left: 1rem" @click="shorten" label="Shorten" rounded />
        </div>
        <Button v-if="show" link :label="shortenedUrl" @click="copy" />
      </template>
    </Card>
  </main>
</template>
<script>
export default {
  data() {
    return {
      url: '',
      shortenedUrl: '',
      show: false
    }
  },
  methods: {
    async shorten() {
      this.show = true
      this.shortenedUrl = await (
        await axios.get(`https://api.shrtco.de/v2/shorten?url=${this.url}`)
      ).data.result.short_link
    },
    copy() {
      navigator.clipboard.writeText(this.shortenedUrl)
    }
  }
}
</script>
