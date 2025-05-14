<script>
let popupDisplay = "none";
let video
let Monuments =[
   [ // No keycard required
    { name: "Abandoned Cabins", img: "Abondoned cabins.webp", vid: "" },
    { name: "Dome", img: "Dome.jpg", vid: "" },
    { name: "Ferry Terminal", img: "ferry terminal.jpg", vid: "" },
    { name: "Junkyard", img: "junkyard.jpg", vid: "" },
    { name: "Lighthouse", img: "lighthouse.jpg", vid: "" },
    { name: "Mining Outpost", img: "mining-outpost.jpg", vid: "" },
    { name: "Oxum's Gas Station", img: "Oxums.jpg", vid: "" },
    { name: "Supermarket", img: "supermarket.jpg", vid: "" },
    { name: "Abandoned Military Base", img: "Abandonded-Military-Base.jpg", vid: "" },
    { name: "Jungle Ziggurat", img:"jungle ziggurat.jpg", vid:""},
],
  [ // Green keycard required
    { name: "Harbor", img: "", vid: "" },
    { name: "Satellite Dish ", img: "", vid: "" },
    { name: "Sewer Branch", img: "", vid: "" },
],
  [ // Blue keycard required
    { name: "Airfield", img: "", vid: "" },
    { name: "Power Plant", img: "", vid: "" },
    { name: "Train Yard", img: "", vid: "" },
    { name: "Water Treatment Plant", img: "", vid: "" },
    { name: "Nuclear Missile Silo", img: "", vid: "" },
    { name: "Arctic Research Base", img: "", vid: "" },
],
  [ // Red keycard required
    
    { name: "Cargo Ship", img: "", vid: "" },
    { name: "Large Oil Rig", img: "", vid: "" },
    { name: "Launch Site", img: "", vid: "" },
    { name: "Military Tunnel", img: "", vid: "" },
    { name: "Small Oil Rig", img: "", vid: "" },
    { name: "Underwater Lab", img: "", vid: "" },
    { name: "Giant Excavator Pit", img: "", vid: "" },
]
]


function Vidpopup(x){
popupDisplay="block";

}
</script>

<svg width="100vw" height="100%" style="position:absolute;opacity:0,5; z-index:1;top:0; left:0; display:{popupDisplay};">
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <rect width="100%" height="100%" style="fill=#000000;" on:click={()=>popupDisplay="none"}></rect>
</svg>
    <rect width="100%" height="100%" filter="url(#noise)" fill="#000000"></rect>
<!-- Monuments -->
<h1 style="position:absolute;top:30%;left:46%;font-size:40px">Tier 0</h1>
<div class="carousel carousel-center rounded-box" style="position: absolute;top:35%;left:10%;width:80%;height:30%">
    {#each Monuments[0] as monument }
    <div class="carousel-item">
        
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
      <img src={monument.img} alt={monument.name} on:click={()=>Vidpopup(monument)}/>
    </div>
    {/each}
</div>
<h1 style="position:absolute;top:70%;left:46%;font-size:40px">Tier 1</h1>
<div class="carousel carousel-center rounded-box" style="position: absolute;top:75%;left:10%;width:80%;height:30%">
    {#each Monuments[1] as monument }
    <div class="carousel-item">
        
      <img src={monument.img} alt={monument.name} />
    </div>
    {/each}
</div>
<h1 style="position:absolute;top:105%;left:46%;font-size:40px">Tier 2</h1>
<div class="carousel carousel-center rounded-box" style="position:absolute;top:110%;left:10%;width:80%;height:30%">
    {#each Monuments[2] as monument }
    <div class="carousel-item">
        
        <img src={monument.img} alt={monument.name} />
    </div>
    {/each}
</div>
<h1 style="position:absolute;top:145%;left:46%;font-size:40px">Tier 3</h1>
<div class="carousel carousel-center rounded-box" style="position: absolute;top:150%;left:10%;width:80%;height:30%">
    {#each Monuments[3] as monument }
    <div class="carousel-item">
        
        <img src={monument.img} alt={monument.name} />
    </div>
    {/each}

</div>

<div style="display: {popupDisplay}; font-family:'Times New Roman', Times, serif;margin: 0;padding: 0;" class="InfoPopup">
    <!-- svelte-ignore missing-declaration -->
    <!-- svelte-ignore a11y-missing-attribute -->
    <iframe width="100%" height="100%" src={video} frameborder="0" allowfullscreen></iframe>
    </div>




<style>

h1,h2,h3{
    color: #ffffff;
    font-family:'Times New Roman', Times, serif;
    text-align: center;
    margin: 0;
    padding: 0;
    
}
.InfoPopup{
    position: fixed;
    top: 6%;
    left: 10%;
    width: 80%;
    height: 90%;
    background-color: #1f1c2b;
    z-index: 10;
    justify-content: center;
    align-items: center;
    border-radius: 20px;
    border: #717171 solid 2px;
}
img{
    height: 100%;
}
</style>
