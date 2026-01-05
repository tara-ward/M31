<template>
  <div class="wrapper" v-cloak :class="{ 'is-previous': isPreviousSlide, 'first-load': isFirstLoad }">
    <div
      class="slide-wrapper"
      v-for="(slide, index) in slides"
      :key="index"
      :class="{ active: index === currentSlide }"
      :style="{
        'z-index': slides.length - index,
        'background-image': 'url(' + slide.bgImg + ')'
      }"
    >
      <div class="slide-inner" @click="updateSlide(index)">
        <div class="slide-bg-text">
          <p>{{ slide.headlineFirstLine }}</p>
          <p v-if="slide.headlineSecondLine">{{ slide.headlineSecondLine }}</p>
        </div>
        <div class="slide-rect-filter">
          <div
            class="slide-rect"
            :style="{ 'border-image-source': 'url(' + slide.rectImg + ')' }"
          ></div>
        </div>
        <div class="slide-content" :class="{ 'has-cards': index === 2, 'has-about': index === 1, 'has-social': index === 4, 'has-home': index === 0 }">
          <div v-if="index === 0" class="home-logo-container" @click.stop>
            <img src="/src/img/M31.png" alt="M31 Logo" class="home-logo" />
          </div>
          <h1 v-if="index === 2" class="projects-title">
            
            <p>{{ slide.headlineFirstLine }}</p>
            <p v-if="slide.headlineSecondLine">{{ slide.headlineSecondLine }}</p>
          </h1>
          <div v-if="index === 1" class="about-me-content" @click.stop>
            <div class="about-box">
              <section class="about-main-content">
                <h1 class="about-title">about me</h1>
                <section class="about-clearfix">
                  <div class="about-col-2 about-egw">
                    <img src="\src\img\author.jpg" alt="Profile"/>
                  </div>
                  <div class="about-col-4 about-info">
                    <p>
                      I am a Canadian fantasy author and winter mythology fanatic. My specialty is winter holiday mythology and magic: Father and Mother Christmas, Krampus, La Befana, Mother Goody, and more.
                      </p>
                      
                      <p>
                      My goal in life is to become the foremost expert in Canadian mythology. As a child, I was largely raised by my Irish gran, who taught me about the many kinds of fairies, pixies, and gnomes. We left appropriate food or small presents whenever we needed their help.
                      </p>
                      
                      <p>
                      My father was a scientist who traveled frequently for consultation work. For much of my childhood, I was left alone for hours in libraries as a form of babysitting. This fostered a tendency to bother librarians and academic dons with questions, as well as a lifelong affinity for books and an aspiration to become a writer.
                      </p>
                      
                      <p>
                      My undergraduate degree is in Narrative Structure and Cinema from the University of Southern California. My graduate degree is in Creative Writing with a focus on Mythology and Folklore from Harvard University. My parents like to tell people I went to Harvard to get a degree in “fairy tales.”
                      </p>
                      
                      <p>
                      The dogs I have loved are the inspiration for many of my animal characters (and handbags). I love dogs and am known for taking in strays, fostering dogs, or helping dogs that friends of friends can no longer keep. At one point, I had ten dogs, none of which were technically mine.
                      </p>
                      
                      <p>
                      Behind every successful woman is a very good dog.
                      </p>
                        
                  </div>
                </section>
              </section>
            </div>
          </div>
          <div v-if="index === 2" class="projects-cards" @click.stop>
            <Card
              data-image="https://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/Card0.png"
            >
              <template #header>
                <h1>Current Work</h1>
              </template>
              <template #content>
                <p>The main project I am currently working on is a twelve-novel series titled <em>The Mauja Le Guin Chronicles</em></p>
              </template>
            </Card>
            <Card
              data-image="https://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/Card3.png"
            >
              <template #header>
                <h1>The Mauja Le Guin Chronicles</h1>
              </template>
              <template #content>
                <p>The first novel in the series, <em>All Is Not Frost</em>, plunges readers into the mystical world of Canadian mythology. Canadian Mauja Le Guin is a thirty-two-year-old, plus-size veterinarian whose mother is the Celtic Goddess of Winter and whose father is a loup garou (werewolf) alpha. Mauja spends her life rescuing wildlife in the human world, until everything changes when she discovers a magical realm parallel to our own called Idavoll.</p>
              </template>
            </Card>
            <Card
              data-image="https://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/Card2.png"
            >
              <template #header>
                <h1>Idavoll and Its Inhabitants</h1>
              </template>
              <template #content>
                <p>
                  During her time in Idavoll, Mauja befriends numerous magical beings, including fairies, the legendary sea monster Ogopogo, Sasquatch, and her trusty sidekick Gerda, a dog-like sentient handbag with infinite holding capacity. She also becomes best friends with Lady Siv, a Nordic goddess whose sentient golden hair, aptly named Hairy, has a talent for kleptomania. With her unique perspective, Mauja serves as a mediator between the magical and human worlds, bridging the conflict and friction between them.
                </p>
              </template>
            </Card>
            <Card
              data-image="https://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/Card1.png"
            >
              <template #header>
                <h1>Snow Place Like Home</h1>
              </template>
              <template #content>
                <p>
                  <em>Snow Place Like Home</em> is a collection of autobiographical short stories unified by their setting during the holiday season and their distinctly Canadian point of view. These pieces are magical nonfiction, drawing from lived experience, ranging from witnessing the launch of the James Webb Space Telescope on Christmas Eve through the Canadian Space Agency to being attacked by U.S. ICE in California. Even when life is difficult, there is magic in the air during the winter holidays.
                </p>
              </template>
            </Card>
          </div>

          <div v-if="index === 3" class="contacts-card" @click.stop style="display: flex; flex-direction: column; align-items: center; min-height: 400px;">
            <h1 class="projects-title">Contact Me</h1>
            <a :href="'mailto:maujaleguin@gmail.com'" target="_blank" rel="noopener">
              <img
                src="/src/img/Email.png"
                alt="Email"
                style="width: 100%; max-width: 900px; cursor: pointer; display: block;"
              />
            </a>
          </div>

          <div v-if="index === 4" class="social-media-content" @click.stop>
            <a href="https://bsky.app/profile/m31author.bsky.social" target="_blank" rel="noopener noreferrer" class="social-media-header">
              <img src="\src\img\Bluesky.png" alt="Bluesky Logo" class="social-media-logo" />
              <span class="social-media-text">M31🍁</span>
            </a>
            <div class="social-media-box">
              <div class="social-media-embed-container">
                <bsky-embed
                  username="m31author.bsky.social"
                  mode="dark"
                  limit="5"
                ></bsky-embed>
              </div>
            </div>
          </div>
        </div>

        <div v-if="index === 5" class="portfolio-santa-paws" @click.stop style="display: flex; flex-direction: column; align-items: center; margin-top: 120px;">
          <img src="/src/img/SantaPaws.png" alt="Santa Paws Top" style="width: 100%; max-width: 700px; object-fit: cover; margin-bottom: 20px; margin-top: -40px; z-index: 1;" />
          <div style="position: relative; width: 100%; max-width: 700px; margin-bottom: 60px;">
            <div style="background: rgba(255,255,255,0.85); border-radius: 16px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); max-height: 300px; overflow-y: auto; padding: 24px; font-size: 1.1rem; color: #333;">
              <p>There once was a wee lass who lived in the Scottish Highlands. Her name was Christmas Cumbersome-Snow. She was named Christmas because she was born on Christmas Eve, and she had two surnames because she had many pretentious ancestors. Christmas - Chris for short - was an only child, and the nearest house with children was twenty-five kilometres away. With no other children to play with, Chris&rsquo;s best mate was a dog named Kringle.</p>
              <p>Kringle was actually a stray half-wolf pup found alone on a fortuitous day. Chris and Kringle grew up together, and Kringle served as playmate, protector, face-taster, and all-round best dog in the whole wide world. Chris and Kringle understood each other so deeply that one would swear Chris could speak wolf.</p>
              <p>Unfortunately, hungry packs of wolves sometimes hunted at dusk, attacking lone animals and people. Chris was adamantly told to NEVER walk farther than the house&rsquo;s fairy lights, as no one could see her in the shadows of the trees. Wolves could attack, and none would be the wiser. Chris knew she was small and chewy, so she tried her best to stay in the light.</p>
              <p>Christmas was Chris&rsquo;s favourite time of year. The fact that she was given loads of presents was dead chuffing, but for Chris, the Highlands became truly a fairyland at Christmas. There was the permeating smell of the shortbread bakery, scurrying pine martens, tinsel-tapered Land Rovers driving up the road, furry cows who couldn&rsquo;t be bothered to stress about shopping, and diamond icing on snow-covered trees. When the snow fell for long days, the water bridge would freeze.</p>
              <p>Reindeer would walk across the water bridge to Scotland from Sweden. It happened every winter; it was how Chris knew Christmas was drawing near. Looking out into the forest, Chris saw the beginning of the reindeer parade, meandering toward her play glen. She had been told to stay away from them because one never knows what a wild animal will do. With the instinct of childish wonder, Chris suspected this was a holiday parade that had something to do with Father Christmas.</p>
              <p>There was shouting coming from the drawing room. Her parents were having a row again. They told Chris this would be her last Christmas in the Highlands, as the family was moving to Canada. Chris cried and begged to stay. She pulled a wobbly, tried reasonable logic-based logarithms, fought physics, and finally tied herself to her favourite tree and shouted, &ldquo;By this living stick, help me, Saint Nick!&rdquo;</p>
              <p>After freezing for several hours and shouting herself hoarse, her father came over wearing a Swiss flag as an armband. He plied her with hot cocoa and Christmas biscuits. He told her that the monarch was interfering with parliamentary proceedings but there was no point in arguing or they could end up with Cromwell, and no one wanted that again. His argument was tasty and seemed legit, so Chris resigned herself to a life of boom diddi ah-daing around a beaver&rsquo;s home. Her father was so relieved at her acquiescence that he untied her from the caber and tossed it.</p>
              <p>It was Christmas Eve, and the shouting was still at a high decibel level as more relatives joined the fray. The house sounded like an out-of-sync cacophony of sleigh bells, as if <em>Carol of the Bells</em> were being performed by first-years. She couldn&rsquo;t stand it one moment longer, so she decided to make like a maple tree and leave.</p>
              <p>Chris and Kringle ran out to the garden, to the edge of the fairy lights. She was far enough from the house that, with the wolves howling, she almost couldn&rsquo;t hear the rumbling sounds of the flagstone fading of losing her home. The worst part of it all was that Kringle could not come with her to Canada. Kringle was half wolf and grew up in the Highlands; he could not leave. Every time she tried to tell Kringle how much she would miss him, she ended up crying instead, and then no words could be formed.</p>
              <p>The tears fell and clumped together, forming icicles like a leaning, frozen thatched roof fighting a fireside. So she decided to complain. Grumbling is the Scottish way, after all.</p>
              <p>&ldquo;In Canada the children are forced to stare at a digital screen all day, attached to one&rsquo;s hand so that wherever one goes the screen always speaks to them,&rdquo; Chris sighed. &ldquo;And they ignore their dogs completely for the screen,&rdquo; she emphasized.</p>
              <p>&ldquo;That sounds terrible,&rdquo; Kringle whined.</p>
              <p>&ldquo;In Toronto the children live in concrete blocks piled as high as mountains. They never leave them because there is no forest or grass to play in - just pavement,&rdquo; Chris complained. &ldquo;To find grass they have to drive around for hours and then pay for parking in order to stop.&rdquo;</p>
              <p>Kringle kept up with Chris, but he was sure Canada was not a place he ever wanted to see, even on holiday, and especially if he were a human child one day. Chris was not even going to mention the moose because it was just one part of Canada. But if a house had Christmas inflatables out front, they would be susceptible to attack from the Santa-hating moose. Or, in winter, one might be chased by moose trying to lick the car.</p>
              <p>Lost in their thoughts, they were both so sad they hadn&rsquo;t noticed they had walked past the fairy lights, and it was quickly growing dark.</p>
              <p>With quick work, the wolves surrounded them. Kringle began to growl and stood in front of Chris, snarling. It did not look good for Chris and Kringle. They were going to be Christmas dinner for the wolves, without the Christmas pudding.</p>
              <p>Suddenly, twelve reindeer surrounded them and pushed the wolves back.</p>
              <p>&ldquo;My my, at Waterloo Napoleon did surrender! Get out of here, and don&rsquo;t come back!&rdquo; the reindeer threatened.</p>
              <p>They were the reindeer from Sweden - one could tell by the accent. The wolves ran away, claiming they had had it with immigrants and were going to vote for Brexit.</p>
              <p>The reindeer were glowing with magical, rainbowed light like the sun rising through a stained-glass window reflected on a disco ball. Chris and Kringle were so relieved they sang Christmas carols, sword-danced a bit, scratched the reindeer on their bottoms, and pondered the contents of fruitcake. The reindeer explained that they were the backup reindeer for Santa&rsquo;s sleigh.</p>
              <p>Christmas Eve was a very busy time, and it was terribly noisy at Father Christmas Headquarters. To get away from the bustle and relax, the reindeer had set up the Highlands as a VIP lounge - a place to chill in case they were called to duty. They were allowed to fly if they were called up, but otherwise they had to walk. Also, a reserve reindeer had not been called up in nearly two hundred years, so they enjoyed eating the Highland grass while they waited. Apparently, Highland grass has a feisty flavour with a smooth whisky aftertaste.</p>
              <p>Chris explained that she was avoiding her house as well. She told the reindeer about the horrors of Canada, and the reindeer countered that the consumerism in North America paid for their pensions, so they weren&rsquo;t bothered by North America. Chris tried not to cry as she explained that she and Kringle were going to be separated by six thousand kilometres of ocean as the reindeer flies. The worst part was that she had no way of knowing whether Kringle would receive a Christmas present every year. Kringle was a very good dog, but Father Christmas was busy and couldn&rsquo;t be expected to ensure all dogs got a gift. The reindeer agreed this was true.</p>
              <p>This was a sticky wicket, like Chris&rsquo;s fingers after eating cinnamon sticky buns and attempting not to stick herself to her teacup.</p>
              <p>Chris had an idea. A plan was forming - her brain synapses firing like a plucky ginger lass with a shotgun. She was Planny Oakley. She confirmed that these twelve reindeer were just reserve reindeer and had not actually done anything meaningful for Christmas in hundreds of years. She confirmed that they all had the ability to fly.</p>
              <p>The reindeer explained that what they did was actually space-temporal distortion - more like time travel than flying. It was complicated, and they had all earned multiple PhDs to get a licence to fly. All the licences came out of London, so the paperwork was unbearable, they grumbled.</p>
              <p>Chris asked if they would be amiable fellows and please, please, <em>please</em> make sure Kringle got his Christmas present next year. She would be ever so grateful and filled with Christmas cheer if they would.</p>
              <p>The reindeer agreed, and everyone was suddenly glittery and glowing with the Christmas spirit.</p>
              <p>It was the Ghost of Christmas Presents.</p>
              <p>Kringle asked about all the other good dogs in the world, and whether <em>they</em> would be receiving gifts this Christmas. The reindeer murmured amongst themselves, noting that everything about this was highly irregular. Kringle explained that they all needed to think outside the Christmas box.</p>
              <p>The reindeer stamped and shuffled, then agreed to let Kringle lead them on an unorthodox pilgrimage. They were going to need Christmas magic and giant safety scissors to cut through the Christmas red tape. But Kringle and the reindeer were going to fly tonight and deliver presents to all the good dogs of the world.</p>
              <p>Chris wanted to come along, but the reindeer said there was no way they could get insurance if an unlicensed human girl tried to fly. Chris pouted but let it go. She headed back toward her house to toddle off to Bedfordshire, because Santa was coming and she did not want to miss her stocking sweets.</p>
              <p>Kringle and the reindeer flew all night, all over the world, spreading Christmas cheer to all the good dogs. Kringle looked quite silly curled up in the driver&rsquo;s seat of the reserve Christmas sleigh. He used the Santa sack as a dog bed, circling it three times before lying down. Kringle was a bit cold, but he liked to stick his head into the wind from time to time and sniff the crisp air.</p>
              <p>The world was still and filled with the bright green silence of Aurora Boring Alice. They delivered gifts, ate the carrots left for them by the children, stole a leftover ham from a Welsh family (well, Kringle did), and made sure every dog had a dental chew for after Christmas breakie.</p>
              <p>When they finally stopped the sleigh ride, the reindeer claimed they couldn&rsquo;t remember the last time they had had so much fun. They made a plan to meet up every year in the Scottish Highlands and deliver gifts to good dogs again. Thus began the legend of Kringle the Santa Paws.</p>
              <p>Years later, after Chris moved to Canada, she continued to tell the story of Santa Paws. She made sure her good dogs were tucked into their beds on Christmas Eve. If a dog did not chew the shoes, eat food off the table, do their business in the house, or sniff the nether regions of the guests, then they would be placed on the good dog list.</p>
              <p>For the good dogs on Christmas Eve, Santa Paws would come and leave a gift under the tree and a dental chew for clean teeth after. Kringle barks as he whisks away on his sleigh:</p>
              <p>&ldquo;Happy Christmas to all the good dogs - now wake up the humans so we can all play!&rdquo;</p>
               
              <div style="height: 200px;"></div>
            </div>
            <img src="/src/img/SantaPaws2.png" alt="Santa Paws Overlay" style="position: absolute; left: 50%; bottom: -140px; transform: translateX(-50%); width: 100%; max-width: 700px; pointer-events: none;" />
          </div>
        </div>

        <h2 class="slide-side-text">
          <span>{{ slide.sublineFirstLine }} / </span>
          <span>{{ slide.sublineSecondLine }}</span>
        </h2>
      </div>
    </div>
    <div class="controls-container">
      <button
        class="controls-button"
        v-for="(slide, index) in slides"
        :key="index"
        :class="{ active: index === currentSlide }"
        @click="updateSlide(index)"
      >
        {{ slide.headlineFirstLine }} {{ slide.headlineSecondLine }}
      </button>
    </div>
    <div class="pagination-container">
      <span
        class="pagination-item"
        v-for="(slide, index) in slides"
        :key="index"
        :class="{ active: index === currentSlide }"
        @click="updateSlide(index)"
      ></span>
    </div>
    <div class="mobile-pagination-container">
      <svg class="mobile-pagination-svg" viewBox="0 0 800 100" preserveAspectRatio="xMidYMid meet">
        <defs>
          <mask :id="'radioMask-' + currentSlide">
            <g :id="'maskGroup-' + currentSlide" fill="#FFF" stroke="#777777" stroke-width="2">
              <circle 
                v-for="(slide, index) in slides" 
                :key="'mask-' + index" 
                :cx="50 + (index * 100)" 
                cy="50" 
                r="15"/>
            </g>
          </mask>
        </defs>
        <g :id="'mainGroup-' + currentSlide" :style="{ mask: `url(#radioMask-${currentSlide})` }">
          <g id="circleGroup" fill="transparent" stroke="#fff" stroke-width="2.5" stroke-miterlimit="10">
            <circle 
              v-for="(slide, index) in slides" 
              :key="'circle-' + index"
              :cx="50 + (index * 100)" 
              cy="50" 
              r="15"
              :class="{ active: index === currentSlide }"
              @click="updateSlide(index)"
              style="cursor: pointer;"/>
          </g>
          <line 
            id="joinLine" 
            fill="none" 
            stroke="#fff" 
            stroke-width="5" 
            stroke-linecap="round" 
            stroke-miterlimit="10" 
            :x1="50 + (currentSlide * 100)" 
            :y1="50" 
            :x2="50 + (currentSlide * 100)" 
            :y2="50"
            class="join-line"/>
        </g>
      </svg>
    </div>
    <div class="mobile-pagination-container">
      <span
        class="mobile-pagination-item"
        v-for="(slide, index) in slides"
        :key="index"
        :class="{ active: index === currentSlide }"
        @click="updateSlide(index)"
      ></span>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch, nextTick } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import Card from './Card.vue'

const router = useRouter()
const route = useRoute()

const currentSlide = ref(0)
const isPreviousSlide = ref(false)
const isFirstLoad = ref(true)

const slides = ref([
  {
    headlineFirstLine: 'Home',
    headlineSecondLine: '',
    sublineFirstLine: 'Welcome',
    sublineSecondLine: 'Home',
    route: '/',
    bgImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide0.png',
    rectImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide-rect0.png'
  },
  {
    headlineFirstLine: 'About',
    headlineSecondLine: '',
    sublineFirstLine: 'M31',
    sublineSecondLine: 'About Me',
    route: '/about',
    bgImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide1.png',
    rectImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide-rect1.png'
  },
  {
    headlineFirstLine: 'Projects',
    headlineSecondLine: '',
    sublineFirstLine: 'My',
    sublineSecondLine: 'Projects',
    route: '/projects',
    bgImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide2.png',
    rectImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide-rect2.png'
  },
  {
    headlineFirstLine: 'Contact',
    headlineSecondLine: '',
    sublineFirstLine: 'Get',
    sublineSecondLine: 'In Touch',
    route: '/contact',
    bgImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide3.png',
    rectImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide-rect3.png'
  },
  {
    headlineFirstLine: 'Social',
    headlineSecondLine: 'Media',
    sublineFirstLine: 'Connect',
    sublineSecondLine: 'With Me',
    route: '/social-media',
    bgImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide4.png',
    rectImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide-rect4.png'
  },
  {
    headlineFirstLine: 'Portfolio',
    headlineSecondLine: '',
    sublineFirstLine: 'My',
    sublineSecondLine: 'Work',
    route: '/portfolio',
    bgImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide5.png',
    rectImg: 'https://raw.githubusercontent.com/tara-ward/M31/refs/heads/mainhttps://raw.githubusercontent.com/tara-ward/M31/refs/heads/main/src/img/slide-rect5.png'
  }
])

// Find current slide index based on route
const getSlideIndexFromRoute = (path) => {
  const index = slides.value.findIndex(slide => slide.route === path)
  return index >= 0 ? index : 0
}

// Watch route changes and update slide
watch(() => route.path, (newPath) => {
  const newIndex = getSlideIndexFromRoute(newPath)
  if (newIndex !== currentSlide.value) {
    isPreviousSlide.value = newIndex < currentSlide.value
    currentSlide.value = newIndex
    isFirstLoad.value = false
  }
}, { immediate: true })

const updateSlide = (index) => {
  isPreviousSlide.value = index < currentSlide.value
  currentSlide.value = index
  isFirstLoad.value = false
  // Navigate to the route
  router.push(slides.value[index].route)
  
  // Animate the join line
  nextTick(() => {
    const joinLine = document.getElementById('joinLine')
    if (joinLine) {
      const newX = 50 + (index * 100)
      joinLine.setAttribute('x1', newX.toString())
      joinLine.setAttribute('x2', newX.toString())
    }
  })
}

onMounted(() => {
  const productRotatorSlide = document.querySelector('.wrapper')
  let startX = 0
  let endX = 0

  productRotatorSlide.addEventListener('touchstart', (event) => {
    startX = event.touches[0].pageX
  })

  productRotatorSlide.addEventListener('touchmove', (event) => {
    endX = event.touches[0].pageX
  })

  productRotatorSlide.addEventListener('touchend', () => {
    const threshold = startX - endX
    if (threshold < 150 && 0 < currentSlide.value) {
      updateSlide(currentSlide.value - 1)
    }
    if (threshold > -150 && currentSlide.value < slides.value.length - 1) {
      updateSlide(currentSlide.value + 1)
    }
  })
})
</script>

<style scoped lang="scss">
@import '../styles/slide-carousel.scss';
</style>

