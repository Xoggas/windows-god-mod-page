<script setup>
import { ref } from 'vue';

import Block from '@/components/Block.vue';
import Gallery from '@/components/Gallery.vue';
import DownloadButton from '@/components/DownloadButton.vue';
import Releases from '@/components/github/Releases.vue';

import sprite1 from '@/assets/images/sprites/1.png';
import sprite2 from '@/assets/images/sprites/2.png';
import sprite3 from '@/assets/images/sprites/3.png';
import sprite4 from '@/assets/images/sprites/4.png';
import sprite5 from '@/assets/images/sprites/5.png';
import sprite6 from '@/assets/images/sprites/6.png';
import chromatics from '@/assets/audio/chromatics.mp3';

const spritePaths = ref([
  sprite1,
  sprite2,
  sprite3,
  sprite4,
  sprite5,
  sprite6
]);
</script>

<template>
  <main>
    <Block>
      <h1 class="header-1">History</h1>
      <p class="paragraph">
        The first instance of this mod being worked on was on October 7th, 2021, when the first track was made for it.
        Though, at the time, the mod was not a final decision and was made for fun. Another track was made on October
        19th, 2021.
      </p>
      <p class="paragraph">
        On November 2nd, 2021, a storyline for the possible mod about WindowsGod2 was made. It would have five weeks
        centered around the idea of depression, and visualizing it with inspiration from We've Destroyed All The Hope In
        This World. Three days later on November 5th, 2021, two game over tracks were made. Two days after that, another
        main track would be made. Five new tracks were made for the mod between November 20th, 2021, and February 7th,
        2022.
      </p>
      <p class="paragraph">
        One of those is Reminiscence on December 16th, 2021, the earliest track to be made that currently appears in the
        mod. On February 11th, 2022, the discord server for the mod would be created, officially making this mod a
        reality. From this point forward until March 10th, 2023, the mod would undergo production and hiatuses. Finally,
        on March 10th, 2023, the official demo of the mod was released on GameBanana, along with its official
        soundtrack. Between the mod's official birth and demo release, forty-two tracks were made, signifying there will
        be a lot of content in the upcoming updates.
      </p>
      <p class="paragraph">
        On May 11th, 2024, a minor update to the mod was released as "Demo 1.01" where some assets were changed. On May
        20th, 2024, a second minor update was released. This new update updates Psych Engine 0.7.3, adds new Geometry
        Dash assets, and Dialogue to the first and only week of the demo.
      </p>
    </Block>
    <Block>
      <h1 class="header-1">Character Information</h1>
      <h2 class="header-2">Appearance</h2>
      <p class="paragraph">
        WindowsGod2 is the main character of the mod. He's depicted as the 111th cube icon in Geometry Dash composed of
        the colors crimson, violet, and navy blue.
        He has two white circles for eyes and a white mouth that change in shape depending on his expression.
        His true origins are unknown, but he was first discovered in a container of green fluid and released by accident
        in January of 2012.
      </p>
      <br>
      <h2 class="header-2">Personality</h2>
      <p class="paragraph">
        WindowsGod2 is rather energetic and outgoing. Generally, he's friendly and spunky and a bit of a "tsundere" when
        put in embarrassing situations that can fluster him. He claims to not enjoy physical affection, but this is
        false.
        He is completely aroace, and feels dissatisfaction in romantic situations to the extent where he will not
        hesitate to act violently in such conditions. This can include verbal, mental, or physical violence.
      </p>
      <br>
      <h2 class="header-2">Abilities</h2>
      <p class="paragraph">
        He can shoot lasers out of the four triangles on the side of his body.
        <br>
        Don&apos;t agitate him!
      </p>
      <br>
      <h2 class="header-2">Stats</h2>
      <p class="paragraph">
        Width - 5cm
        <br>
        Length - 18cm
        <br>
        Height - 18cm
      </p>
      <br>
      <h2 class="header-2">Gallery</h2>
      <Gallery :paths="spritePaths" />
    </Block>
    <Block>
      <h1 class="header-1">Downloads</h1>
      <DownloadButton :href="chromatics">
        <p>Download chromatics</p>
      </DownloadButton>
    </Block>
    <Block>
      <h1 class="header-1">Releases</h1>
      <Releases />
    </Block>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>