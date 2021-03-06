<template>
  <div class="about-page">
    <header-section showNavSearch="true"></header-section>
    <main role="main" class="margin-normal">
      <h2 role="article">{{ $t('about.title') }}</h2>
      <i18n path="about.description.content" tag="p">
        <template v-slot:link>
          <a
            :aria-label="$t('about.aria.licenses')"
            href="https://creativecommons.org/share-your-work/licensing-examples/"
            >{{ $t('about.description.licenses-link') }}</a
          >
        </template>
      </i18n>
      <i18n path="about.collection" tag="p">
        <template v-slot:common-crawl>
          <a aria-label="common crawl" href="http://commoncrawl.org/"
            >Common Crawl</a
          >
        </template>
      </i18n>
      <i18n path="about.planning.content" tag="p">
        <template v-slot:vision>
          <a
            :aria-label="$t('about.aria.vision')"
            href="https://creativecommons.org/2019/03/19/cc-search/"
            >{{ $t('about.planning.vision') }}</a
          >
        </template>
        <template v-slot:roadmap>
          <a
            :aria-label="$t('about.aria.roadmap')"
            href="https://docs.google.com/document/d/19yH2V5K4nzWgEXaZhkzD1egzrRayyDdxlzxZOTCm_pc/edit#heading=h.jih78emira0r"
            >{{ $t('about.planning.roadmap') }}</a
          >
        </template>
        <template v-slot:working>
          <a
            :aria-label="$t('about.aria.projects')"
            href="https://github.com/orgs/creativecommons/projects/7"
            >{{ $t('about.planning.working') }}</a
          >
        </template>
        <template v-slot:search>
          <a
            aria-label="cc search repository"
            href="https://github.com/creativecommons/cccatalog-frontend/"
            >{{ $t('about.planning.search') }}</a
          >
        </template>
        <template v-slot:catalog-api>
          <a
            aria-label="cc catalog-api repository"
            href="https://github.com/creativecommons/cccatalog-api/"
            >{{ $t('about.planning.catalog-api') }}</a
          >
        </template>
        <template v-slot:catalog>
          <a
            aria-label="cc catalog repository"
            href="https://github.com/creativecommons/cccatalog/"
            >{{ $t('about.planning.catalog') }}</a
          >
        </template>
        <template v-slot:community>
          <a
            :aria-label="$t('about.aria.contribution')"
            href="https://creativecommons.github.io/contributing-code/"
            >{{ $t('about.planning.community') }}</a
          >
        </template>
      </i18n>
      <i18n path="about.declaration.content" tag="p">
        <template v-slot:terms>
          <a
            :aria-label="$t('about.aria.terms')"
            href="https://creativecommons.org/terms/"
            >{{ $t('about.declaration.terms') }}</a
          >
        </template>
      </i18n>
      <i18n path="about.old-cc-search" tag="p">
        <template v-slot:link>
          <a
            :aria-label="$t('about.aria.old-cc-search')"
            href="https://oldsearch.creativecommons.org"
            >https://oldsearch.creativecommons.org</a
          >
        </template>
      </i18n>
      <h3 class="margin-vertical-normal">{{ $t('about.sources') }}</h3>
      <table
        :aria-label="$t('about.aria.sources')"
        role="region"
        class="table is-bordered is-striped"
      >
        <thead>
          <th>{{ $t('about.providers.source') }}</th>
          <th>{{ $t('about.providers.domain') }}</th>
          <th>{{ $t('about.providers.work') }}</th>
        </thead>
        <tbody>
          <tr
            role="row"
            v-for="(imageProvider, index) in imageProviders"
            :key="index"
          >
            <td>{{ imageProvider.display_name }}</td>
            <td>
              <a
                :aria-label="imageProvider.display_name"
                :href="imageProvider.source_url"
              >
                {{ imageProvider.source_url }}
              </a>
            </td>
            <td class="number-cell">
              {{ getProviderImageCount(imageProvider.image_count) }}
            </td>
          </tr>
        </tbody>
      </table>
    </main>
    <footer-section></footer-section>
  </div>
</template>

<script>
import HeaderSection from '@/components/HeaderSection'
import FooterSection from '@/components/FooterSection'
import ServerPrefetchProvidersMixin from '@/pages/mixins/ServerPrefetchProvidersMixin'

const AboutPage = {
  name: 'about-page',
  mixins: [ServerPrefetchProvidersMixin],
  components: {
    HeaderSection,
    FooterSection,
  },
  computed: {
    imageProviders() {
      return this.$store.state.imageProviders
    },
  },
  methods: {
    getProviderImageCount(imageCount) {
      return imageCount.toLocaleString('en')
    },
  },
}

export default AboutPage
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../styles/text-only-page.scss';
</style>
