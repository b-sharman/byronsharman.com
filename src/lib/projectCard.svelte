<script lang='ts'>
import type { Project } from "$lib/types.ts";
import { slide } from "svelte/transition";

interface Props {
  project: Project;
}

let { project }: Props = $props();
</script>

<li in:slide={{duration: 150}} out:slide={{duration: 325}} class="overflow-hidden border border-gray-200 rounded-xl sm:min-w-[250px] flex flex-col size-full rounded-xl">

  <div class="p-4">
    {#if project.image !== undefined}
      <img
        alt={project.image.alt}
        class="object-contain max-h-60 mx-auto mb-4 sm:float-right sm:max-w-72 sm:ml-4 aspect-[{project.image.width/project.image.height}]"
        loading="lazy"
        src={project.image.path}
      />
    {/if}
    <h3 class="font-bold text-xl mb-2">
      {project.name}
      {#if project.hackathonName !== undefined}
        <span class="font-normal text-gray-600">{`[${project.hackathonName}]`}</span>
      {/if}
      {#if project.name === 'byronsharman.com'}
        <span class="font-normal text-gray-600">{`(this website!)`}</span>
      {/if}
    </h3>
    <p class="text-sm text-gray-600 mb-4">{project.languages.join(', ')}</p>
    <div class="prose max-w-max">{@html project.description}</div>
  </div>

  <a href={project.url} class="group flex justify-end items-center bg-gray-200">
    <div class="m-2 sm:m-3 flex">
      <div class="flex items-center px-4">
        <p class="text-sm">{project.bottomText}</p>
      </div>
      <div class="flex place-items-center w-6">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="relative left-0 group-hover:left-1 size-4 transition-all duration-100">
          <path stroke-linecap="round" stroke-linejoin="round" d="m8.25 4.5 7.5 7.5-7.5 7.5" />
        </svg>
      </div>
    </div>
  </a>

</li>
