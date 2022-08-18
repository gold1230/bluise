<template>
  <section class="home">
    <div class="py-24 md:py-36 mx-auto flex flex-wrap flex-col md:flex-row items-center">
      <div class="flex flex-col w-full xl:w-3/5 justify-center lg:items-start overflow-y-hidden">
        <div v-html="$md.render(welcomeText)" class="home__welcome markdown" />
          <p>
          Why You Should Visit Morocco and Learn About Moroccan Culture and People

Despite its relatively small area (roughly the same as California), Morocco has a long and fascinating history. In the last century alone, Morocco has been a French colony and a Spanish protectorate.

Moroccans remain among of the world's kindest and most hospitable people despite a long history of strangers swooping in and Arabizing, then westernizing, their original Berber traditions. Any visitor who has visited Morocco will tell you that the people there are some of the friendliest and most welcoming in the world.

Plan a trip to Morocco. Learn About Morocco's Rich History and <a href="https://moroccoexpedition.com/">Friendly People Tours</a> may be scheduled by calling (800) 787-8806. Contact us and we'll help you plan your trip to Morocco.

Most people think of Morocco as an Arab country, but that's not accurate. Although it is true that the majority of Moroccans are Muslims, the country is more accurately defined as a mix of Arabs and Berbers. Moroccans trace their ancestry back to a people group called the Berbers. At the end of the seventh century, the Arabs came, having already conquered most of North Africa and the Middle East in the service of their new revolutionary creed, Islam. Nearly all Berbers eventually became Muslims, and their newfound faith was welcomed by their Arab neighbors. Muslims from Morocco conquered the Iberian peninsula, and the majority of their army were Berbers. Eventually, the two cultures blended.

Most Moroccans nowadays may trace their history back to both the Arab world and the Berber region, although there is a small minority (particularly among the Shereefs, who trace their lineage back to the Prophet Mohammed and are given the honorific "Moulay") who insist on their exclusivity as Arabs. However, there are still pockets of unmixed Berbers in the Rif and Atlas Mountains as well as the Souss Valley, where their old languages are still spoken (Tarfit, spoken by 1.5 million people in the Rif; Tamazight, spoken by over 3 million people in the Atlas; and Teshalhit, spoken by 3-4 million people in the Souss Valley region). The traditional sense of pride among Berbers has recently been revived. Although the majority of the population speaks Arabic, TV shows are increasingly aired in Berber languages and the languages are taught in schools.

The history of the Berber people is shrouded in mystery, however it has been speculated that they may have come from either modern-day Yemen or Syria. Because of the high rate of intermarriage between the Berber and Arab communities throughout the centuries, visitors to Morocco shouldn't be shocked to see numerous people with green or blue eyes and pale complexion.

Because the Berber language never established a writing system, it is difficult to pinpoint when the Berbers first arrived in Morocco. Three civilizations had an impact on the Berbers before the Arabs came in the 7th century: the Phoenicians, the Carthaginians, and the Romans. The Berbers fought the Romans more than any of the other tribes mentioned, although the others had little effect on their culture. The three years and 20,000 men it took to put down one insurrection between them is a good example.

The Arabs who came in 680 B.C. were more aggressive than earlier waves and succeeded in making the nation Arab and Muslim. If you ever find yourself in Morocco, you should go there to experience the fruition of their efforts. Currently, the majority of Moroccans (99%) are Berber Muslims.

Islam's rapid expansion in North Africa in the 12th century drove the indigenous Berbers to the region's mountainous interior. When they moved to a new area, the Berbers, whose name means "those who are not Arab," found that they did not fit in with the fast-paced, hectic way of life of their new neighbors. As a result, they left the plains and cities behind for the peace and quiet of the mountains, where they adopted an agricultural and nomadic way of life.

Despite Morocco's successful conversion to a Muslim nation, its new leaders faced decades of problems, including civil war, insurrection, outmoded ways of administration, and widespread dissatisfaction. Because of this, Europeans, especially Spanish and Portuguese, started showing up in Morocco.

Even after Morocco declared bankruptcy at the end of the 19th century, Spain and France remained engaged in an effort to ease the country's economic woes. By signing the Treaty of Fes (1912), Morocco accepted the protection of Spain and France. The treaty was in effect for forty years and contributed to Morocco's status as a colony of France. Morocco regained its independence from France in 1956.

A country's language reveals much about its culture and people. When you go to Morocco, you'll see firsthand how the Europeans influenced Moroccan culture and politics. These days, French is the de facto working language of Morocco's government, companies, and diplomatic ties with other countries. Spanish is widely spoken in the north of the nation. While 70% of the people is fluent in Arabic, the official language, 30% speak one of the 300 Berber languages.

Of the total population, over 33% are members of the Amaziah, the rural Berber groups that may still be found in the country and the highlands. But in the last several decades, more Berbers have moved into metropolitan regions in quest of a better living, drawn there by the promise of a western-style education.

Visitors to Morocco will see the three Berber communities (the Ruffians in the north, the Chleuhs in the middle and high Atlas, and the Soussi in the southwest) living in harmony with the country's Arab and minor Jewish populations, both of whom have called Morocco home since the 15th century.

The peaceful coexistence of people of very diverse cultural and religious traditions in Morocco is an inspiration. In addition to Arabs, Berbers, and Jews, many British, French, and American expats live and work in the South for the government in positions such as teaching, technology, and business administration.

Morocco's long history of foreign domination and influence has given its people some of the world's greatest communication and tolerance abilities. Your trip will undoubtedly be life-changing, leaving you with a strong desire to return.
          </p>
        <div class="mb-12 xl:mb-0">
          <h4 v-if="isSignedUp">Thank you - we'll be in touch shortly.</h4>

         
        </div>
      </div>
      <div class="flex flex-col w-full xl:w-2/5">
        <img
          alt="Hero"
          class="rounded shadow-xl"
          src="https://source.unsplash.com/random/720x400"
        />
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import settings from '@/content/settings/general.json';

@Component({
  // Called to know which transition to apply
  transition() {
    return 'slide-left';
  },
})
export default class Home extends Vue {
  welcomeText = settings.welcomeText;

  get posts(): Post[] {
    return this.$store.state.posts;
  }

  isSignedUp = false;

  form = {
    email: '',
  };

  encode(data): string {
    return Object.keys(data)
      .map((key) => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`)
      .join('&');
  }

  validEmail(email): boolean {
    // eslint-disable-next-line
    const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(email);
  }

  async handleSubmit(): Promise<void> {
    if (!this.validEmail(this.form.email)) {
      this.$refs.emailInput.focus();
      return;
    }

    try {
      await fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({ 'form-name': 'signups', ...this.form }),
      });

      this.isSignedUp = true;
    } catch (error) {
      console.error(error);
    }
  }
}
</script>
