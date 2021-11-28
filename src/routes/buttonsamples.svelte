<script>
  import Button from '$lib/svelte-daisy/Button.svelte'
</script>
Sizes
<div class="divider"/> 
<Button sm>Small</Button>
<Button btn-sm>Small</Button>
<div class="divider"/> 
<Button>Normal</Button> aka Medium
<div class="divider"/> 
<Button btn-lg>Large</Button>
<div class="divider"/> 
<Button btn-wide>Wide</Button>
<div class="divider"/> 
<Button btn-block>Block</Button>
<div class="divider"/> 
Styles
<div class="divider"/> 
<Button btn-xs btn-outline>XSmall outline</Button><br>
<div class="divider"/> 
<Button btn-wide btn-outline btn-error>Wide error</Button>
<div class="divider"/> 
Button with icon<br><br>
<Button>
  <svg class="fill-current w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z"/></svg>
  <span>Download</span>
</Button>
