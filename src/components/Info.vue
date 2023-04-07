<script setup>
import InfoItem from './InfoItem.vue'
import Projects from './Projects.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <InfoItem>
    <template #icon>
      <DocumentationIcon id="education" />
    </template>
    <template #heading>Education</template>
    <ul>
        <li>Student at TUB (🇩🇪 Technical University of Berlin), 10/2018 entry, BSc in CE.</li>
        <li><div class="bold">Fields of Interest: </div>Embedded Systems and Automation Technology.</li>
    </ul>
  </InfoItem>

  <InfoItem>
    <template #icon>
      <ToolingIcon id="work" />
    </template>
    <template #heading>Work Experience</template>
    *crickets* hire me, please 🥺.
  </InfoItem>

  <InfoItem>
    <template #icon>
      <SupportIcon id="projects" />
    </template>
    <template #heading>Personal Projects</template>
    <Projects />
  </InfoItem>

  <InfoItem>
    <template #icon>
      <CommunityIcon id="contact" />
    </template>
    <template #heading>Contact</template>
    <li><div class="bold">E-mail: </div><a href="mailto:test@gmail.com">test@gmail.com</a></li>
  </InfoItem>
</template>
