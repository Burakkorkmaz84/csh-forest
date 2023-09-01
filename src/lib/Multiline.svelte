<script>
    import * as Plot from "@observablehq/plot";
    import * as d3 from "d3";

    import {selectedId} from '../stores/ui.js';

    export let data;

    export let selectedT;
    
    // export let selectedId = null;

    function lines(node) {
        node.appendChild(
            Plot.plot({
            marks: [
                Plot.ruleY([0]),
                Plot.lineY(data, { 
                    x: "t", y: "r", z: "id", 
                    stroke: d=> d.id == $selectedId ? "red": "#333",
                    opacity: d=> d.id == $selectedId ? 1: 0.3
                })
            ]
            })
        )
    }
</script>

{#key $selectedId}
    <div use:lines ></div>
{/key}