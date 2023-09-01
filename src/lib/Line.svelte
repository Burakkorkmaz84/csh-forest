<script>
    import * as Plot from "@observablehq/plot";
    import * as d3 from "d3";

    import {selectedId} from '../stores/ui.js';
	import Page from "../routes/+page.svelte";

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
                   ...options,
                    // stroke: d=> d.id == $selectedId ? "red": "#333",
                    // opacity: d=> d.id == $selectedId ? 1: 0.3
                }),
                Plot.dot(data,{...options, fill:d=>d.t==selectedT? 'red':'none'})
            ]
            })
        )
    }
</script>
<!-- <div use:lines></div> -->
{#key selectedT}  
    <div use:lines></div>
{/key}
