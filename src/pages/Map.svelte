<script>
	import Map from "ol/Map";
	import View from "ol/View";
	import GeoJSON from "ol/format/GeoJSON";
	import TileLayer from "ol/layer/Tile";
	import VectorLayer from "ol/layer/Vector";
	import { fromLonLat } from "ol/proj";
	import OSM from "ol/source/OSM.js";
	import VectorSource from "ol/source/Vector";
	import { Fill, Style } from "ol/style";
	import { onMount } from "svelte";
	onMount(async () => {
		new Map({
			target: "m_A_p",
			layers: [
				new TileLayer({
					source: new OSM(),
				}),
				new VectorLayer({
					source: new VectorSource({
						format: new GeoJSON(),
						url: "countries.json",
					}),
					style: new Style({
						fill: new Fill({
							color: "rgba(0, 106, 78, 0.75)", // Set the color to #006a4e with 0.75 opacity
						}),
					}),
				}),
			],
			view: new View({
				center: fromLonLat([90.4104271, 23.8137154]),
				zoom: 4,
			}),
		});
	});
</script>

<section id="m_A_p" class="w-full h-[calc(100vh-84px)]" />
