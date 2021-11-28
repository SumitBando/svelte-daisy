<!--
 @component
 A Svelte wrapper around DaisyUI Alert.
 
 Use:
 ```code
  <Alert>Lorem sit amet</Alert>
  <Alert info>Info</Alert>
  <Alert success>Success</Alert>
  <Alert warning>Warning</Alert>
  <Alert error>Error</Alert>
  <Alert error icon>Error</Alert>
 ```
-->
<script>
  const extractUtility = (/** @type {string[]} */ utilities) => {
    let utility = ''
    utilities.forEach(u => {
      if ($$props[u]) {
        if (utility) console.log('overriding spec ', utility, ' with ', u)
        if (!u.startsWith('alert-')) u = 'alert-' + u
        utility = u
      }
    })
    console.log('extractUtility attr', utilities, utility)
    return utility
  }
  const makeAlertList = (/** @type {string[]} */ utilities) => 
    utilities.map((e) => { return [e, 'alert-' + e] }).flat();

  const colors = ['info', 'success', 'warning', 'error']
  const color = extractUtility(makeAlertList(colors))

  import {Info, Success, Warning, Error} from '$lib/svelte-daisy/icons'
  let leftIcon = null
  const showIcon = $$props['icon']
  if (showIcon) {
  if (color == 'alert-info') leftIcon = Info
  else if (color == 'alert-success') leftIcon = Success
  else if (color == 'alert-warning') leftIcon = Warning
  else if (color == 'alert-error') leftIcon = Error
  }
</script>

<div class={`alert ${color}`}>
	<div class="flex-1">
    <svelte:component this={leftIcon}/>
		<!-- svelte-ignore a11y-label-has-associated-control -->
		<label><slot/></label>
		<!-- svelte-ignore a11y-label-has-associated-control -->
	</div>
	<slot name="right" class="flex-none"/>
</div>
