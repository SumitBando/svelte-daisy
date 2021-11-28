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
        if (!u.startsWith('btn-')) u = 'btn-' + u
        utility = u
      }
    })
    // console.log('extractUtility attr', utilities, utility)
    return utility
  }

  const makeButtonList = (/** @type {string[]} */ utilities) => 
    utilities.map((e) => { return [e, 'btn-' + e] }).flat();
  
  const sizes = ['lg', 'md', 'sm', 'xs', 'wide', 'block'];
  const size = extractUtility(makeButtonList(sizes))

  const shapes = ['circle', 'square']
  const shape = extractUtility(makeButtonList(shapes))

  const colors = ['primary', 'secondary', 'accent', 'info', 'success', 'warning', 'error']
  const color = extractUtility(makeButtonList(colors))

  let styles = ['ghost', 'link', 'outline', 'active', 'disabled']
  styles.push('glass', 'loading', 'no-animation')
  const style = extractUtility(makeButtonList(styles))
	// console.log({ $$props, size, shape, color, style });
</script>

<!-- <button class="btn">Normal</button> 
<button class="btn btn-md">Medium</button>  -->

<button class={`btn ${size} ${shape} ${color} ${style}`}><slot>Button</slot></button>