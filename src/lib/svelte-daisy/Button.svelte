<!--
 @component
 A Svelte wrapper around DaisyUI Button.
 Checks for conflicting specifications
 
 Use:
 - \<Button>Normal\</Button> (a.k.a md or Medium)
 - \<Button btn-sm>Small\</Button>
 - \<Button btn-lg>Large\</Button>
-->
<script>
  const extractUtility = (/** @type {string[]} */ utilities) => {
    let utility = ''
    utilities.forEach(u => {
      if ($$props[u]) {
        if (utility) console.log('overriding spec ', utility, ' with ', u)
        utility = u
      }
    })
    // console.log('extractUtility attr', utilities, utility)
    return utility
  }

  const sizes = ['btn-lg', 'btn-md', 'btn-sm', 'btn-xs', 'btn-wide', 'btn-block'];
  const size = extractUtility(sizes)
  const shapes = ['btn-circle','btn-square']
  const shape = extractUtility(shapes)
  const colors = ['btn-primary', 'btn-secondary', 'btn-accent', 'btn-info', 'btn-success', 'btn-warning', 'btn-error']
  const color = extractUtility(colors)
  const styles = ['btn-ghost', 'btn-link', 'btn-outline', 'btn-active', 'btn-disabled', 'glass', 'loading', 'no-animation']
  const style = extractUtility(styles)
	// console.log({ $$props, size, shape, color, style });
</script>

<!-- <button class="btn">Normal</button> 
<button class="btn btn-md">Medium</button>  -->

<button class={`btn ${size} ${shape} ${color} ${style}`}><slot>Button</slot></button>