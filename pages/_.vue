<template>
  <div>
    <div>
          <section class="flex items-center justify-center h-64 bg-transparent">
      <img
        :src="'/images/covers/'+article.cover"
        :alt="article.title"
        class="absolute top-48 w-64 -translate-y-32 mt-5 mb-5"
      />
    </section>
    </div>
    <div>
        <div class="px-4 mx-auto sm:px-6 xl:max-w-7xl xl:px-0 mt-20">
    <h1 class="text-4xl text-gray-700 font-extrabold mb-10 text-center">
      {{ article.title }}
    </h1>

    <div class="grid grid-cols-3 text-center w-1/2 mx-auto">
      <div class="mobile-responsive">
        <p class="text-center font-bold my-5 text-slate-400 text-xs">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
          </svg>
          {{ formatDate(article.date) }}
        </p>
      </div>
      <div class="mobile-responsive">
        <p class="text-center font-bold my-5 text-slate-400 text-xs">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
          {{ article.readTime.text }}
        </p>
      </div>
      <div class="flex items-center font-medium sm:mx-3 justify-center mobile">
        <nuxt-img
          :src="siteMetadata.author_image"
          loading="lazy"
          alt=""
          class="mr-3 w-10 h-10 dark:bg-slate-800"
        />
        <div>
          <div class="font-bold text-slate-400 text-xs">
            {{ siteMetadata.author }}
          </div>
          <a
            target="_blank"
            :href="siteMetadata.github"
            class="font-bold text-sky-400 text-xs hover:text-sky-600"
          >
            @{{ siteMetadata.twitter_user }}
          </a>
        </div>
      </div>
    </div>
    <div class="w-1/2 mx-auto">
      <div class="mt-2 text-xs my-3 flex flex-wrap -m-1 justify-center">
        <p v-for="tag in article.tags" :key="tag"
           class="m-1 leading-loose text-slate-400 border border-current lowercase px-2 rounded font-medium">
          #{{ tag }}
        </p>
      </div>
    </div>


    <div class="text-left mx-auto">
      <div class="flex flex-wrap lg:flex-row-reverse py-12">
        <div class="w-full lg:w-1/4 px-5" v-if="article.toc.length > 0">
          <PageSidebar :toc="article.toc" />
        </div>

        <div class="w-full px-5 max-w-none centered-image" :class="article.toc.length > 0  ? 'lg:w-3/4 ' : ''">
          <nuxt-content id="nuxtContent" class="prose font-proxima text-xl font-medium min-w-full mx-auto" :document="article" />
        </div>
      </div>
    </div>



    <hr class="mb-12">

    <div>

      <span>
      Arkada??lar??nla Payla??...
      </span>
      <div class="mt-4">

        <a :href="'https://facebook.com/sharer/sharer.php?u='+ this.postLink" target="_blank" rel="noopener" aria-label="">
          <button type="button" class="text-white bg-[#3b5998] hover:bg-[#3b5998]/90 focus:ring-4 focus:outline-none focus:ring-[#3b5998]/50 font-medium rounded-lg text-sm px-3 py-3 text-center inline-flex items-center dark:focus:ring-[#3b5998]/55 mr-2 mb-2">
            <svg class="w-6 h-6" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="facebook-f" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 320 512"><path fill="currentColor" d="M279.1 288l14.22-92.66h-88.91v-60.13c0-25.35 12.42-50.06 52.24-50.06h40.42V6.26S260.4 0 225.4 0c-73.22 0-121.1 44.38-121.1 124.7v70.62H22.89V288h81.39v224h100.2V288z"></path></svg>
          </button>
        </a>

        <a :href="'https://twitter.com/share?url=' + this.postLink + '&text=' + article.title +'&via='+ siteMetadata.twitter_user" target="_blank" title="Share on Twitter" rel="noopener noreferrer">
        <button type="button" class="text-white bg-[#1da1f2] hover:bg-[#1da1f2]/90 focus:ring-4 focus:outline-none focus:ring-[#1da1f2]/50 font-medium rounded-lg text-sm px-3 py-3 text-center inline-flex items-center dark:focus:ring-[#1da1f2]/55 mr-2 mb-2">
          <svg class="w-6 h-6" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="twitter" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M459.4 151.7c.325 4.548 .325 9.097 .325 13.65 0 138.7-105.6 298.6-298.6 298.6-59.45 0-114.7-17.22-161.1-47.11 8.447 .974 16.57 1.299 25.34 1.299 49.06 0 94.21-16.57 130.3-44.83-46.13-.975-84.79-31.19-98.11-72.77 6.498 .974 12.99 1.624 19.82 1.624 9.421 0 18.84-1.3 27.61-3.573-48.08-9.747-84.14-51.98-84.14-102.1v-1.299c13.97 7.797 30.21 12.67 47.43 13.32-28.26-18.84-46.78-51.01-46.78-87.39 0-19.49 5.197-37.36 14.29-52.95 51.65 63.67 129.3 105.3 216.4 109.8-1.624-7.797-2.599-15.92-2.599-24.04 0-57.83 46.78-104.9 104.9-104.9 30.21 0 57.5 12.67 76.67 33.14 23.72-4.548 46.46-13.32 66.6-25.34-7.798 24.37-24.37 44.83-46.13 57.83 21.12-2.273 41.58-8.122 60.43-16.24-14.29 20.79-32.16 39.31-52.63 54.25z"></path></svg>
        </button>
        </a>





      </div>
    </div>

    <div class="pt-16" v-if="relatedArticles.length > 0">
      <div class="text-xl font-semibold">??nerilen Bloglar :</div>
      <div class="pt-10 grid lg:grid-cols-3 md:grid-cols-2 sm:grid-cols-1 gap-4 text-center w-3/4 mx-auto">

        <HomeBlogCard v-for="article in relatedArticles"
                  :key="article.id"
                  :title="article.title"
                  :img="'/covers/'+article.cover"
                  :description="article.description"
                  :date="article.date"
                  :slug="article.slug"
                  :tags="article.tags"
                  :path="article.path"
        />
      </div>
    </div>
    </div>
    </div>

  </div>
</template>
<script>
import Prism from "~/plugins/prism";
import siteMetaInfo from "@/data/sitemetainfo";
import HeroSection from "~/components/Common/HeroSection";

export default {
  data() {
    return {
      title: 0,
      siteMetadata: siteMetaInfo,
    };
  },
  async asyncData({ $content, params}) {
    const article = await $content("articles", params.pathMatch, { deep: true }).fetch();
    let allRelatedArticles = [];

    if (article.tags) {
      for (let i = 0; i < article.tags.length; i++) {
        const tag = article.tags[i];

        let looker = $content("articles", {deep: true}, params.slug)
          .only([
            "id",
            "title",
            "description",
            "img",
            "slug",
            "tags",
            "author",
            "date",
            "draft",
            "path",
            "cover"
          ])
          .sortBy("date", "desc")
          .where( {tags: { $contains: tag }, title: { $ne: article.title } } )
        const relatedArticles = await looker.fetch();

        relatedArticles.forEach(article => {
          var isAlreadyIn = allRelatedArticles.find(function(element) {
            return element.id === article.id;
          });
          if (!isAlreadyIn) {
            allRelatedArticles.push(article);
          }
        });

      }
    }

    let shuffledRelatedArticles = allRelatedArticles
      .map(value => ({ value, sort: Math.random() }))
      .sort((a, b) => a.sort - b.sort)
      .map(({ value }) => value)
      .slice(0, 3);

    return {
      article: article,
      relatedArticles: shuffledRelatedArticles,
    };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("tr", options);
    },
  },

  computed : {
    postLink() {
      return this.siteMetadata.siteUrl  + this.article.path.replace('/articles', '');
    },

  },

  head() {
    return {
      title: this.article.title + " | " + siteMetaInfo.title,
    };
  },
};
</script>
<style>
.nuxt-content h2 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content p {
  margin-bottom: 20px;
}

@media screen and (max-width: 768px) {
  .mobile-responsive{
    display: none;
  }
  .mobile{
    position: relative;
    margin: auto;
    margin-left: 50%;
  }
}

</style>
