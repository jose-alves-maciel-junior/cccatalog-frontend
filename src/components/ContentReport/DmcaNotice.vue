<template>
  <div>
    <i18n
      path="photo-details.content-report.dmca.content"
      tag="span"
      class="is-block padding-horizontal-big margin-top-large has-text-centered"
    >
      <template v-slot:link>
        <a
          :aria-label="$t('photo-details.aria.dmca')"
          :href="dmcaFormUrl"
          target="_blank"
          rel="noopener"
          >DMCA form</a
        >
      </template>
    </i18n>
    <i18n
      path="photo-details.content-report.dmca.provider"
      tag="span"
      class="is-block padding-horizontal-big margin-top-large has-text-centered"
    >
      <template v-slot:link>
        <a
          :aria-label="provider + 'form'"
          :href="imageURL"
          target="_blank"
          rel="noopener"
          >{{ providerName }}</a
        >.
      </template>
    </i18n>
    <button
      class="button is-text tiny margin-top-normal is-shadowless has-text-grey"
      @click="onBackClick()"
    >
      <span
        ><i class="icon chevron-left margin-right-small"></i>
        {{ $t('photo-details.content-report.back') }}</span
      >
    </button>
  </div>
</template>

<script>
export default {
  name: 'dmca-notice',
  props: ['dmcaFormUrl', 'imageURL', 'providerName'],
  methods: {
    onBackClick() {
      this.$emit('onBackClick')
    },
  },
}
</script>
