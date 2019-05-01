<template>
  <div class="container">
    <progressive-img class="content-image" :src="img" />
    <img class="home-button" :class="{ disabled: main }" src="/static/icons/home.svg" @click="() => navigate('home')" />
    <span class="image-description" :class="{ disabled: description.length === 0 }">{{description}}</span>
    <div class="content">
      <div class="controls" :class="{ disabled: main }">
        <img src="/static/icons/left-arrow.svg" @click="previousImage"/>
        <span class="counter">{{area ? `${imageIndices[area]} of ${imageLengths[area]}` : null}}</span>
        <img src="/static/icons/right-arrow.svg" @click="nextImage"/>
      </div>
      <h1>{{title}}</h1>
      <p v-html="content"></p>
      <div class="places">
        <ImageButton src="/static/tb/1.jpeg" text="Tiong Bahru" :onClick="() => navigate('tb')" />
        <ImageButton src="/static/dc/1.png" text="Dakota Crescent" :onClick="() => navigate('dc')" />
        <ImageButton src="/static/ks/1.jpeg" text="Kampung Silat" :onClick="() => navigate('ks')" />
      </div>
    </div>
  </div>
</template>

<script>
import ImageButton from './ImageButton.vue'

const originalTitle = 'SIT Flats'
const originalContent = 'Exploring the architectural designs and policies of the Singapore Improvement Trust (SIT) Flats, and investigating the difference in repurposings of the flats.<br /><ol><li>Some images on the left can be scrolled</li><li>Click on any image below to start</li><li>Supporting commentary is given to provide insight</li><li>Some images can be quite large, please wait warmly for them to load!</li><li>We also like to put out a disclaimer that we are not professional photographers but we try our best!<li>All of the photos we took are available <a target="_blank" href="https://drive.google.com/drive/folders/181DZrJQYRQalXI6n1V5f7IxvCCaB5NIs?usp=sharing">here</a></li>'

export default {
  name: 'HelloWorld',
  components: { ImageButton },
  data () {
    return {
      main: true,
      title: originalTitle,
      img: '/static/1.webp',
      content: originalContent,
      description: '',
      area: 'main',
      imageIndices: { 'tb': 1, 'dc': 1, 'ks': 1 }
    }
  },
  props: {
    imageLengths: {
      type: Object,
      default: () => ({ 'tb': 13, 'dc': 18, 'ks': 10 })
    },
    descriptions: {
      type: Object,
      default: () => (
        {
          'dc': [
            'Dakota Crescent was built in 1958, modelled after British towns and adapted to suit the tropical climate. In 2017, it was announced by the government that the cluster with the central courtyard will be repurposed for civic and community usage.',
            'To be torn down to make way for new flats, the windows on the first floors are boarded up to prevent illegal entry.',
            'The other courtyard that is not slated for preservation. It lies unkempt, but we still noticed a family coming over to play badminton after we were done photographing the area.',
            '(Scrollable) Some ornaments can still be seen hung on the ceiling. The brickwork is also substantially different from the HDB flats we see nowadays, with the brick pattern visible from afar. A ramp has also been added into the structure retroactively, catering to the ageing population in the area.',
            '(Scrollable) Close up look at the different grille designs. Wear and tear caused by the elements would prompt the owners to replace their grilles.',
            'Different types of window installations can be seen here. We can also see the zinc plating under the bamboo pole holders, which is not found in HDB flats as they tend to corrode easily. However, it was prime material back then as it was considerably cheaper than steel.',
            'The back view of one of the 3-storey buildings with its unique tesellating pattern. This stretch is to be demolished.',
            'Leftover clothes pegs from the previous owner.',
            'We did not manage to take a photo of the full view of Block 12 as there was a Malay wedding shoot, but that shoot took place with this brick pattern as the backdrop.',
            '(Scrollable) These lifts do not stop on every floor. Also, since they were built back in 1958, there are very few engineers now that are able to repair it.',
            '(Scrollable) Owners took to their hands to repaint or even rebuild the balcony doors to fit their personas.',
            'Due to poorer drainage systems in the past, we can imagine that the lifts are placed on higher grounds to possibly prevent them from getting flooded during the monsoon sesasons. The "butterfly" design, with the blocks bending at 90 degrees was supposedly to help with the ventilation.',
            '',
            '(Scrollable) A Karung Guni or a homeless person repurposed the space illegally to store their wares. We also noted that the temporary abandonment and ruination brings across a new dynamic in the ecosystem, with a clearly larger pigeon population and vagrants.',
            'This is one of the low-rise stretches that is slated for preservation, designed differently. The first floor was previously commercialized as shops but have since closed, pending repurposing.',
            'Stairs leading to the second floor, which was the residential area. We would have liked to go in and explore but the entrance was locked. ',
            '(Scrollable) The stairwell of one of the buildings slated for preservation.',
            'The famous Dove playground to be preserved, as we imagine old playgrounds from the past would present a higher nostalgic factor to future homeowners. It is part of the central courtyard in between four blocks that form a square around it, and this concept is one of the very few remaining in Singapore.'
          ],
          'tb': [
            '(Scrollable) Tiong Bahru is famous to tourists and Singaporeans alike for shophouses that sell exquisite products that may not be found elsewhere in Singapore',
            'Shops are accommodating to tourists as shown from the multilingual sign in Chinese, Japanese and English (in the middle of the photo)',
            'Tourists roaming around the area was a common sight, sporting sleeveless attires due to the hot and humid weather in Singapore.',
            '(Scrollable) One of the remaining SIT flats. Residents on the upper floors redesigned the windows, while the ones on the ground floor remained unchanged. This creates a dissonance in the overall aesthetics of the building.',
            '',
            'A single road separates condominiums (left), HDB Flats (center) as well as SIT flats (right).',
            '',
            'Apartments in a flat separated by a single staircase that could barely fit 2 people width-wise. We could hear the racket caused by the families with small children as we took this photo.',
            '(Scrollable) A landmark in SIT flats - the spiral staircase leads directly to the entrances of the apartments, although some seemed to be boarded up for good',
            '',
            'The reconstructed Community Centre. It was originally built to host activities to promote kinship among neighbours.',
            'A close-up picture of the Community Centre in the past. The area it occupies has since expanded to accommodate more facilities for the public',
            ''
          ],
          'ks': [
            'Melati and Kemuning (the one behind) are the Spooner Road flats. They originally belongs to KTM as quarters for their workers. It was handed over to Singapore Land Authority (SLA) in 2011.',
            'Kampong Silat Estate was one of the pioneering SIT estates. The construction commenced in 1948 and was scheduled to complete by 1949. However, due to the climate issue which posed a challenge to the construction process, it was only completed in 1952. We can see the remaining few buildings in the distance.',
            'View of the last 5 flats under construction.',
            'Kampong Silat has been repurposed to be a nursing home, and then replaced by Lee Ah Mooi Old Age Home in 2017, renovating the area to provide more amenities to the people in need.',
            'A snapshot of how the flats looks like. You can see that while there are works done between the flats, the flats are kept the way they were.',
            'An aerial view from the 8th floor of a neighbouring flat.',
            'In the year 2007, the 13 flats were included in the Selective En Bloc Redevelopment Scheme (SERS) program. By 2012, most of the residents were relocated to new flats somewhere else (Remember Singapore, 2012)',
            'This place is going to have a condominium together with the five conserved flats. To the right, the residential area will be connected to the Rail Corridor.',
            'An aerial view from 8th floor of a neighbouring flat.',
            'A chinese temple in the neighbourhood. The close proximity to the housing flats provides the convenience for the residents.'
          ]
        }
      )
    },
    contents: {
      type: Object,
      default: () => (
        {
          'dc': [
            'The SIT structures act as memory using a semiotics lens - it registers what happens to its inhabitants, and the use of these buildings creates a materialization of memory - it provides an escape to a distant past, bringing out good memories in an exercise of involuntary nostalgia.',
            '',
            'From Maurice Halbwach’s La Mémoire collective, besides having individual memory, a society can have a collective memory. This means that the individual is able to adopt the collective memory created by the environment he/ she lives in.',
            'Members of the public welcome the Government\'s notion to retain parts of the estate, but want a more pre-emptive measure to lobby for conservation instead of a reactive one. The people cited different needs based on their professions - the heritage group\'s president suggested for an aesthetically interpretive way to portray the past, while the property agent is looking for avenues of profit.<br/><a target="_blank" href="https://www.todayonline.com/singapore/partial-conservation-dakota-crescent-gives-heritage-enthusiasts-hope">https://www.todayonline.com/singapore/partial-conservation-dakota-crescent-gives-heritage-enthusiasts-hope</a><br/><br/>The need to preserve heritage and the need to "capitalize" prime land is a delicate balance, but how much is to be preserved and how much to destroy?',
            'As Dakota Crescent is near the central area of Singapore, it seems that the conservation status of these areas pushes up their demand even further. It makes these housing estates to be of higher value in terms of price and also social status. Of course, real-estate agents will not leave out these reasons when selling these houses to clients. Some people might not be buying these houses due to the “right reason”, which is to conserve them.<br/><blockquote>“Some homebuyers could also be drawn to the area due to fond memories of growing up there” - Real Estate Officer Eugene Lim</blockquote>',
            'The government decided to retain a cluster of flats in Dakota Crescent after encountering opposition from residents, and even the area’s Member of Parliament, Mr Lim Biow Chuan (Mountbatten) had “called for the estate to be conserved” and “made an impassioned plea for the authorities to reconsider redevelopment plans”. There are also talks about democratizing the decision for housing redevelopments, i.e. allow the community to provide feedback and suggestions.',
            'If the government allows for the democratization of decisions regarding housing estates, it is better able to serve the needs of its people (or dwellers) as compared to if the estates are privately owned and are more likely to succumb wholly on commercial reasons. In this case, while it is arguable that the government still takes a more economic stance on housing estate developments, it is still trying to take its citizens’ voice into account and make a compromise based on that.',
            '',
            '',
            '',
            '',
            '',
            '',
            '',
            'However, there seems to be some form of conflict of interest: the estates are not only treated as preservation sites, but also being commercialized by being put up for sale. By subjecting the buildings as private commodities, this was at odds with the preservation status of being a national or public good, which was described by URA to “retain the inherent spirit and original ambience of historic buildings”, and requiring “an appreciation and understanding of the architecture and structure of historic buildings” - the former part felt wanting with the commercialization. ',
            '',
            '',
            'The playground was designed by Mr <a target="_blank" href="https://www.esplanade.com/tributesg/administrators/khor-ean-ghee">Khor Ean Ghee</a>, who also designed other animal themed playgrounds in other areas in Singapore. A similar design may trigger collective nostalgia in the community.<br/>Consequently, these landmarks become “Sites of Memory” for the people (Pierre Noa, Les Lieux de Mémoire). The intersection between memory and history creates reference points, which becomes part of the nation’s official history.'
          ],
          'tb': [
            'It can be said that commercialisation for tourism can be due to “pragmatic economic reasons” as it brings about revenue for the country. That said, it can also mean that the preservation is due to the exploitation of local features of historical, cultural and scenic interest.',
            '',
            'The treatment of landmarks as being heritage sites is often done by the process of Museumification. As a result, much of the site might become fake and man-made/ mock-ups. As such, it might not be as full of the vibrant life in the history it actually aimed to depict. For the SIT flats, the impact seems quite minimal. In Tiong Bahru, only a small area is being repurposed for businesses, restaurants and cafes. It is only in these places that we can argue that much of the setting is highly artificial, preservation with commercial utility.',
            'Most of Tiong Bahru is actually kept intact, remaining as housing estates. There are still many people living in these flats, especially elderly residents, so it does not seemed to be museumified at this very moment.',
            '<blockquote>“The Past is a foreign country” - David Lowenthal</blockquote>However, as more newer residents start to move in and more areas possibly repurposed, museumification might start to happen more and more. It will render the past to be quite quaint or foreign. Food for thought: But what can we really do if we reach a point where there is no one from that distant past to continue living in these areas?<blockquote><a href="https://www.todayonline.com/singapore/noise-issue-tiong-bahru-most-residents-peace-businesses-estate" target="_blank">URA replacing first floor residentials in Tiong Bahru for commercial use</a>',
            '<b>Is it necessarily a bad thing that the flats are preserved because of commercial reasons?</b>',
            'A prime example of the Streamline Moderne style:<ul><li>clean, curved shapes and rounded corners</li><li>long horizontal and vertical lines</li><li>simple, uncluttered lines</li><li>bands of windows</li><li>flat roofs</li><li>racing stripes to simulate speed and motion</li><li>glass blocks and group windows</li></ul>The flats\' curved corners and cantilevered shades convey a modern yet pleasing appearance. As early residents thought the design of some blocks looked like the wings of an aeroplane, these flats were also called "aeroplane flats".',
            'Even if the sustenance of preservation efforts are driven by economic reasons, we cannot simply deny that there may be some positive aspects to it. The act of preservation allows for a sense of national identity and an avenue of nostalgia as discussed in the earlier parts. The crucial thing is that some form of “genuine love” for the historic past of the SIT flats needs to exist in their management in the long run, otherwise the flats will just eventually become an artificial entity that acts as merely a money-making machine.',
            '<b>Then, why are some of the SIT flats being torn down?</b><blockquote>“This popular acceptance of ‘survival through pragmatism’ is primarily grounded in the tangible results of the ‘practical’ policies of the government: that is, the policies have ‘delivered the goods’. Any social repression that attends these policies is seen as politically essential to continuing economic growth; this is the bargain the electorate makes with the PAP government.” - Chua B.H, Political Legitimacy and Housing: Stakeholding in Singapore</blockquote>',
            'We have to keep the strategy that the long-running party in the government takes in its policy-making in mind. Economic growth triumphs any form of social repercussions in terms of nostalgia.',
            'The flats nearby are promoted as heritage sites with even “Heritage Trails” that one can follow by finding information boards situated beside key landmarks.',
            '',
            'After discussing the several reasons why some of the SIT flats are being preserved, it is logical to argue for the following reasons:<ol><li>There are already SIT flats as heritage sites for tourism, there is simply no need to have so many of them, especially since there is a lack of space in Singapore.</li><li>At first, the direct decision under the reformation of Dakota and Kampong Silat was complete renovation, meaning the SIT flats residing in these areas would be completely torn down and make way for new buildings, HDB flats or condominiums. The decision to keep only some is primarily due to the opposition from the people due to nostalgia. As such, a practical compromise is to allow just some flats to be preserved while repurposing and tearing down the others.</li></ol>'
          ],
          'ks': [
            '<blockquote>“it should be recognized that every state intervention is necessarily a political act”- Chua Beng Huat, Political Legitimacy and Housing: Stakeholding in Singapore</blockquote>In Singapore’s case, there’s such a heavy involvement of government intervention in public housing that it is can be synonymous with government housing. This is where the politics of housing comes in. ',
            'It also can be said that the policy-making of public housings are part of a bigger plan for social engineering, which necessitates careful decision-makings with regards to the HDB and SIT flats. Some policies include the race ratios imposed on the flats and planning for improvements or redevelopment of estates. Therefore, a lot of oikopolitical programming seems to be involved.',
            'Now that we established the fact that the government is the primary authority regarding the decision of preservation, just what are they trying to achieve here besides economic progress?',
            '<blockquote>Perhaps one pressing reason is to “maintain ideological hegemony or, in its own terminology, to achieve ideological consensus on issues that surround a particular provision as a social need” (Chua, Political Legitimacy and Housing). </blockquote>This applies not only to the provision of housing alone, but also to the preservation of the old SIT estates as well. It needs to be able to continue having this ideological hegemony/ consensus in the long run when dealing with housing policies, therefore there cannot be a major resistance. For instance, it cannot just carry on with its redevelopment plan of SIT flats if there are any form of strong opposition that the economic justification cannot outweigh the social impacts.',
            '',
            '',
            '',
            '',
            '',
            ''
          ]
        }
      )
    }
  },
  methods: {
    setContent: function () {
      this.content = this.contents[this.area] ? this.contents[this.area][this.imageIndices[this.area] - 1] : ''
      this.description = this.descriptions[this.area] ? this.descriptions[this.area][this.imageIndices[this.area] - 1] : ''
    },
    previousImage: function () {
      if (this.imageIndices[this.area] === 1) {
        this.imageIndices[this.area] = this.imageLengths[this.area]
      } else {
        this.imageIndices[this.area] -= 1
      }
      this.img = `/static/${this.area}/${this.imageIndices[this.area]}_ex.webp`
      this.setContent()
    },
    nextImage: function () {
      if (this.imageIndices[this.area] === this.imageLengths[this.area]) {
        this.imageIndices[this.area] = 1
      } else {
        this.imageIndices[this.area] += 1
      }
      this.img = `/static/${this.area}/${this.imageIndices[this.area]}_ex.webp`
      this.setContent()
    },
    navigate: function (type) {
      this.area = type
      if (type === 'tb') {
        this.main = false
        this.img = '/static/tb/1_ex.webp'
        this.title = 'Tiong Bahru'
        this.imageIndices[type] = 1
        this.setContent()
      } else if (type === 'dc') {
        this.main = false
        this.img = '/static/dc/1_ex.webp'
        this.title = 'Dakota Crescent'
        this.imageIndices[type] = 1
        this.setContent()
      } else if (type === 'ks') {
        this.main = false
        this.img = '/static/ks/1_ex.webp'
        this.title = 'Kampung Silat'
        this.imageIndices[type] = 1
        this.setContent()
      } else {
        this.main = true
        this.img = '/static/1.webp'
        this.title = originalTitle
        this.content = originalContent
      }
    }
  }
}
</script>

<style scoped>
.home-button {
  position: absolute;
  right: 12px;
  top: 22px;
  width: 32px;
  cursor: pointer;
  z-index: 2;
}

.home-button:hover {
  opacity: 0.5;
}

.home-button.disabled:hover {
  opacity: 0;
}

.disabled {
  opacity: 0;
  cursor: initial;
}

.controls {
  position: absolute;
  top: 22px;
  left: -150px;
  z-index: 2;
  padding: 6px 0 6px 3px;
  background-color: rgba(255,255,255,0.5);
  display: flex;
  flex-direction: row;
  align-items: center;
}

.image-description {
  position: absolute;
  z-index: 2;
  bottom: 64px;
  width: 600px;
  padding: 32px;
  text-align: left;
  left: 0;
  background-color: rgba(255,255,255,0.8);
}

.image-description.disabled {
  opacity: 0;
}

.controls img {
  width: 32px;
  cursor: pointer;
}

.container {
  min-height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.content {
  display: flex;
  flex-direction: column;
  width: 490px;
  position: relative;
  text-align: left;
}

.places {
  display: flex;
  margin-top: auto;
  flex-direction: row;
  justify-content: space-around;
  align-items: flex-end;
  width: 100%;
  text-align: center;
}

h1 {
  width: 100%;
  text-align: center;
}

p {
  margin: 40px;
}

.content-image {
  overflow: auto;
  height: 100vh;
}

</style>
