<script setup>
  import InfoItem from './InfoItem.vue'
  import Projects from './Projects.vue'
  import DocumentationIcon from './icons/IconDocumentation.vue'
  import ToolingIcon from './icons/IconTooling.vue'
  import CommunityIcon from './icons/IconCommunity.vue'
  import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <InfoItem  id="education">
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Education</template>
    <ul>
        <li>Student at TUB (🇩🇪 Technical University of Berlin), 10/2018 entry, BSc in CE.</li>
        <li><div class="bold">Fields of Interest: </div>Embedded Systems and Software Developmet.</li>
    </ul>
  </InfoItem>

  <InfoItem id="work">
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Work Experience</template>
    *crickets* hire me, please 🥺.
  </InfoItem>

  <InfoItem id="projects">
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Personal Projects</template>
    <Projects />
  </InfoItem>

  <InfoItem id="contact">
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>Contact</template>
    <li><div class="bold">E-mail: </div><a href="mailto:nganhuyennguyenthi@gmail.com">nganhuyennguyenthi@gmail.com</a></li>
  </InfoItem>
</template>
