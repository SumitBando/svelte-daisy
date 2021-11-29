<script>
  import Alert from '$lib/svelte-daisy/Alert.svelte'
</script>

<Alert>Generic</Alert>
<div class="divider"/> 
<Alert alert-info>Info</Alert>
<div class="divider"/> 
<Alert info>Simpler info</Alert>
<div class="divider"/> 
<Alert info icon>Info with icon</Alert>
<div class="divider"/> 
<Alert alert-success>Success</Alert>
<div class="divider"/> 
<Alert alert-warning icon>Warning with icon</Alert>
<div class="divider"/> 
<Alert alert-error>Error</Alert>
<div class="divider"/>
<Alert>
  Error message
  <span slot="right">
    <button class="btn btn-sm btn-ghost mr-2">Cancel</button> 
    <button class="btn btn-sm btn-primary">Apply</button>
  </span>
</Alert>
