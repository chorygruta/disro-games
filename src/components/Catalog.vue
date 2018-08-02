<template>
  <v-container fluid class="pa-0">
    <v-container text-xs-center fluid grid-list-lg class="pa-2">
      <v-layout row wrap align-center>
        <v-flex d-flex lg4 md4 xs12 class="pb-0 pt-3 ma-0">
          <v-select
            content-class="default-class select-content-list"
            dark
            max-height="500"
            color="white"
            box
            background-color="deep-purple accent-2"
            :items="categories"
            label="Browse All Games"
            solo
            prepend-inner-icon="person"
          ></v-select>
        </v-flex>
        <v-flex d-flex lg12 md12 xs12 class="pt-0">
          <v-container text-xs-center fluid grid-list-xs class="pa-0">
            <v-layout row wrap>
              <!-- For Desktop -->
              <v-flex hidden-sm-and-down lg3 md3 xs6 v-for="game in games" :key="game.title">
                <v-card ripple class="catalog-tile">
                  <v-card-media
                    height="25vw"
                    :src="game.image"
                  >
                  </v-card-media>
                  <v-divider color="lavender"></v-divider>
                  <v-card-title class="text-xs-left pa-3">
                    <div>
                      <span>{{ game.title }}</span><br>
                    </div>
                  </v-card-title>
                </v-card>
              </v-flex>
              <!-- For Mobile  -->
              <v-flex hidden-md-and-up sm6 xs6 v-for="game in games" :key="game.title">
                <v-card class="catalog-tile">
                  <v-card-media
                    height="50vw"
                    :src="game.image"
                  >
                  </v-card-media>
                  <v-divider color="lavender"></v-divider>
                  <v-card-title class="text-xs-left pa-2">
                    <div>
                      <span>{{ game.title }}</span><br>
                    </div>
                  </v-card-title>
                </v-card>
              </v-flex>
            </v-layout>
          </v-container>
        </v-flex>
      </v-layout>
    </v-container>
  </v-container>
</template>

<script>
  export default {
    name: 'Catalog',
    data: () => ({
      categories: ['Browse All Games', 'Adventure', 'Action', 'Role-playing', 'Simulation', 'Strategy', 'Sports'],
      games: [{
        image: 'https://upload.wikimedia.org/wikipedia/en/thumb/f/fd/Call_of_Duty_-_Infinite_Warfare_%28promo_image%29.jpg/220px-Call_of_Duty_-_Infinite_Warfare_%28promo_image%29.jpg',
        title: 'Call of Duty: Infinite Warfare'
      }, {
        image: 'https://mediaexpert.pl/suppliers/images/35/758/884/5/7588845_0.jpg',
        title: 'Call of Duty: Modern Warfare Remastered'
      }, {
        image: 'data:image/jpeg;base64,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',
        title: 'Halo 5: Guardians'
      }, {
        image: 'https://upload.wikimedia.org/wikipedia/en/thumb/f/ff/Gears_of_War_4.jpg/220px-Gears_of_War_4.jpg',
        title: 'Gears of War 4'
      }, {
        image: 'https://images-eds-ssl.xboxlive.com/image?url=8Oaj9Ryq1G1_p3lLnXlsaZgGzAie6Mnu24_PawYuDYIoH77pJ.X5Z.MqQPibUVTcPtB7yoM7YK7A6apJBrPMegD8P2blNMraGLQbUdWTEHRXR7OCwpY0JAwdc1rRxRlfYhNIZGZ0sFeJFOJ2oID2EIs.7ojB9huGIxdKvnEqU0TvtCHWigh91tnXYEPR8KZnmfB6d3RZGxmJcW8tfX4_zSBw6P5z8WKzxrdwuEUs9PA-&w=200&h=300&format=jpg',
        title: 'Mortal Kombat X'
      }, {
        image: 'https://upload.wikimedia.org/wikipedia/en/thumb/a/a2/Super_Smash_Bros_for_Wii_U_Box_Art.png/220px-Super_Smash_Bros_for_Wii_U_Box_Art.png',
        title: 'Smash 4'
      }]
    })
  }
</script>

<style scoped lang="scss">
  .catalog-tile {
    border-radius: 6px;
    background-color: #1c1f2a !important; // override .light theme
    color: #D1C4E9 !important;
    font-size: 1.2em !important;
    height: 100% !important;
  }
</style>
