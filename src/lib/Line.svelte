<script>
    import * as Plot from "@observablehq/plot";
    import * as d3 from "d3";

    import {selectedId} from '../stores/ui.js';

    export let data;
    export let options;

    export let selectedT;

    function lines(node) {
        node.appendChild(
            Plot.plot({
            width: 900,
            height: 200,
            marks: [
                Plot.ruleY([0]),
                Plot.lineY(data, { 
                   ...options
                    // stroke: d=> d.id == $selectedId ? "red": "#333",
                    // opacity: d=> d.id == $selectedId ? 1: 0.3
                })
            ]
            })
        )
    }
</script>
<div use:lines></div>
