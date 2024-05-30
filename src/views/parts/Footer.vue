<script setup>
import { ref } from 'vue';

import Social from '@/components/Social.vue';

import GmailIcon from '@/assets/icons/gmail.svg';
import YoutubeIcon from '@/assets/icons/youtube.svg';
import DiscordIcon from '@/assets/icons/discord.svg';

const gmailLink = ref(import.meta.env.VITE_GMAIL_LINK);
const youtubeLink = ref(import.meta.env.VITE_YOUTUBE_CHANNEL_LINK);
const discordLink = ref(import.meta.env.VITE_DISCORD_SERVER_LINK);
</script>

<template>
  <footer>
    <p>Copyright &copy; 2024 WindoniaWorkz&trade;</p>
    <p>No material may be reproduced without written permission.</p>
    <div class="socials">
      <Social :icon="GmailIcon" :link="gmailLink" />
      <Social :icon="YoutubeIcon" :link="youtubeLink" />
      <Social :icon="DiscordIcon" :link="discordLink" />
    </div>
  </footer>
</template>

<style scoped>
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  gap: 1.25em;
  background-color: var(--main-color-2);
  padding: 3.5em 0;
  border-top-color: var(--border-color-2);
  border-top-width: 0.5px;
  border-top-style: solid;
}

p {
  font-size: 1em;
  font-weight: 200;
  color: var(--text-color-2);
}

.socials {
  display: flex;
  gap: 1.25em;
}
</style>