<script lang="ts">
  import { clsx } from 'clsx'
  import {onMount} from "svelte";

  type Color = 'yellow' | 'green' | 'orange' | 'blue'
  type Variant = 'invert-y' | 'invert-x' | 'invert-xy' | 'hidden' | 'normal'

  export let size: 's' | 'm' | 'l' | 'xl' | '2xl' | '3xl' = 'm'
  export let color: Color
  export let variant: Variant = 'normal'
  export let animate: boolean = false
  export let col: number = 0

  let start = false

  onMount(() => {
    setTimeout(() => {
      start = true
    }, col * 100)
  })
</script>

<div class="p-0.5 group" {...$$props}>
  <svg
    width="280"
    height="282"
    viewBox="0 0 280 282"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    class={clsx(
      'h-auto',
      color === 'yellow' ? 'text-brand-yellow' :
      color === 'green' ? 'text-brand-green' :
      color === 'blue' ? 'text-brand-blue' :
      'text-brand-orange',
      size === 'm' ? 'w-16' :
      size === 'l' ? 'w-32' :
      size === 'xl' ? 'w-64' :
      size === '2xl' ? 'w-[32rem]' :
      size === '3xl' ? 'w-[64rem]' :
      'w-8',
      variant === 'invert-y' ? 'scale-y-[-1]' :
      variant === 'invert-x' ? 'scale-x-[-1]' :
      variant === 'invert-xy' ? 'scale-x-[-1] scale-y-[-1]' :
      variant === 'hidden' ? 'hidden' :
      undefined,
      animate ? `duration-200 transform-gpu ${
        ['invert-x', 'invert-xy'].includes(variant) ? 'group-hover:scale-x-[1]' : 'group-hover:scale-x-[-1]'
      }` : undefined,
      animate && !start ? 'scale-x-[0]' : undefined,
    )}
  >
    <path d="M233.235 105.043C231.607 106.53 231.607 108.941 233.235 110.419L253.541 128.892V128.908L266.929 141.105C275.298 148.723 279.999 159.056 279.999 169.831V239.23C279.999 262.749 259.047 281.825 233.21 281.825H152.702C170.456 273.934 175.987 255.807 177.003 249.307V231.685C177.003 223.104 184.382 216.089 193.682 215.623C194.01 215.599 194.345 215.591 194.681 215.591C199.088 215.591 203.117 217.061 206.215 219.496L217.992 230.215C219.62 231.702 222.264 231.702 223.893 230.215C225.521 228.729 225.521 226.326 223.893 224.839L203.722 206.479L190.333 194.282C181.964 186.665 177.263 176.331 177.263 165.556V117.024C177.263 106.241 181.754 95.8593 189.838 87.9688L279.999 0V101.082C279.999 101.211 279.999 101.331 279.991 101.468C279.806 109.262 273.888 115.762 265.922 117.635C264.42 117.988 262.85 118.173 261.23 118.173C256.621 118.173 252.399 116.662 249.134 114.147L246.884 112.09L239.145 105.043C237.516 103.557 234.864 103.557 233.235 105.043Z" fill="currentColor"/>
    <path d="M168.882 117.026V242.366C168.882 264.157 149.474 281.827 125.534 281.827H0L54.6878 228.465C62.2509 221.081 72.7352 216.79 83.7902 216.493H127.398C129.698 216.493 131.57 214.789 131.57 212.692C131.57 210.595 129.698 208.892 127.398 208.892H114.211C106.924 208.369 100.965 203.532 99.4201 197.192C99.1599 196.14 99.0256 195.047 99.0256 193.922C99.0256 190.13 100.268 186.956 102.375 183.999C104.776 180.64 107.688 177.032 110.475 174.019L168.882 117.026Z" fill="currentColor"/>
  </svg>
</div>
