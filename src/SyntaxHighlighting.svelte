<script>
  import { onDestroy, onMount } from 'svelte';
  import DmnModeler from 'dmn-js/lib/Modeler';

  import {
    DecisionTableSyntaxHighlighting,
    LiteralExpressionSyntaxHighlighting
  } from 'dmn-js-syntax-highlighting';

  export let xml;

  let modeler;

  onMount(() => {
    modeler = new DmnModeler({
      common: {
        codeEditor: {
          autocomplete: false
        }
      },
      decisionTable: {
        additionalModules: [
          DecisionTableSyntaxHighlighting
        ]
      },
      literalExpression: {
        additionalModules: [
          LiteralExpressionSyntaxHighlighting
        ]
      },
      container: '#container'
    });

    modeler.importXML(xml);
  });

  onDestroy(() => modeler.destroy());
</script>

<div id="container"></div>
