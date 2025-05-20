<script>
let popupDisplay = "none";
let video
let Monuments =[
   [ // No keycard required
    { name: "Abandoned Cabins", img: "Abondoned cabins.webp", vid: "" },
    { name: "Dome", img: "Dome.jpg", vid: "" },
    { name: "Ferry Terminal", img: "ferry.jpg", vid: "" },
    { name: "Junkyard", img: "junkyard.jpg", vid: "" },
    { name: "Lighthouse", img: "lighthouse.jpg", vid: "" },
    { name: "Mining Outpost", img: "mining-outpost.jpg", vid: "" },
    { name: "Oxum's Gas Station", img: "Oxums.jpg", vid: "" },
    { name: "Supermarket", img: "supermarket.jpg", vid: "" },
    { name: "Abandoned Military Base", img: "Abandonded-Military-Base.jpg", vid: "" },
    { name: "Jungle Ziggurat", img:"jungle ziggurat.jpg", vid:""},
],
  [ // Green keycard required
    { name: "Harbor", img: "harbor.jpg", vid: "" },
    { name: "Satellite Dish ", img: "Satallite-Dish.jpg", vid: "" },
    { name: "Sewer Branch", img: "Sewer-Branch-Monument.jpg", vid: "" },
],
  [ // Blue keycard required
    { name: "Airfield", img: "airfield.png", vid: "" },
    { name: "Power Plant", img: "Power_Plant.webp", vid: "" },
    { name: "Train Yard", img: "trainyard.png", vid: "" },
    { name: "Water Treatment Plant", img: "watertreat.avif", vid: "" },
    { name: "Nuclear Missile Silo", img: "missile silo.jpg", vid: "" },
    { name: "Arctic Research Base", img: "arcticbase.jpg", vid: "" },
],
  [ // Red keycard required
    
    { name: "Cargo Ship", img: "cargo.webp", vid: "" },
    { name: "Large Oil Rig", img: "Loil.jpg", vid: "" },
    { name: "Launch Site", img: "launch.webp", vid: "" },
    { name: "Military Tunnel", img: "tunnels.jpg", vid: "" },
    { name: "Small Oil Rig", img: "smoil.png", vid: "" },
    { name: "Underwater Lab", img: "labs.jpg", vid: "" },
    { name: "Giant Excavator Pit", img: "excav.webp", vid: "" },
]
]


function Vidpopup(x){
popupDisplay="block";
video = x.vid;
}
</script>

<svg width="100vw" height="100%" style="position:absolute;opacity:0,5; z-index:1;top:0; left:0; display:{popupDisplay};">
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <rect width="100%" height="100%" style="fill=#000000;" on:click={()=>popupDisplay="none"}></rect>
</svg>
    <rect width="100%" height="100%" filter="url(#noise)" fill="#000000"></rect>

<!-- Monuments -->
<h1 style="position:absolute;top:20%;left:46%;font-size:40px">Tier 0</h1>
<div style="position: absolute;top:19%;left:54%;font-size:40px" class="tooltip" data-tip="Tier 0 Monuments are the most basic monuments. They do not require any keycards to access.">
    <button class="btn">!</button>
</div>
<div class="carousel carousel-center rounded-box" style="position: absolute;top:28%;left:10%;width:80%;height:30%">
    {#each Monuments[0] as monument }
    <div class="carousel-item">
        
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
      <img src={monument.img} alt={monument.name} on:click={()=>Vidpopup(monument)}/>
    </div>
    {/each}
</div>

<h1 style="position:absolute;top:60%;left:46%;font-size:40px">Tier 1</h1>
<div style="position: absolute;top:59%;left:54%;font-size:40px" class="tooltip" data-tip="Tier 1 are the second most basic monuments. They require a green keycard aswell as a fuse to access.">
    <button class="btn">!</button>
</div>
<div class="carousel carousel-center rounded-box" style="position: absolute;top:65%;left:10%;width:80%;height:30%">
    {#each Monuments[1] as monument }
    <div class="carousel-item">
        
      <img src={monument.img} alt={monument.name} />
    </div>
    {/each}
</div>

<h1 style="position:absolute;top:96%;left:46%;font-size:40px">Tier 2</h1>
<div style="position: absolute;top:95%;left:54%;font-size:40px" class="tooltip" data-tip="Tier 2 Monuments require a blue keycard aswell as a fuse to access. In some cases such as the Power Plant or Airfield, you will also need a green keycard.">
    <button class="btn">!</button>
</div>
<div class="carousel carousel-center rounded-box" style="position:absolute;top:101%;left:10%;width:80%;height:30%">
    {#each Monuments[2] as monument }
    <div class="carousel-item">
        
        <img src={monument.img} alt={monument.name} />
    </div>
    {/each}
</div>

<h1 style="position:absolute;top:135%;left:46%;font-size:40px">Tier 3</h1>
<div style="position: absolute;top:134%;left:54%;font-size:40px" class="tooltip" data-tip="Tier 3 monuments are the highest tier of monuments with the best loot such as locked crates, Most of them require all three cards to access however cargo doesnt take any cards the same goes for excavator.">
    <button class="btn">!</button>
</div>
<div class="carousel carousel-center rounded-box" style="position: absolute;top:140%;left:10%;width:80%;height:30%">
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

h1{
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
    z-index: 10;
    justify-content: center;
    align-items: center;
    border-radius: 20px;

}
img{
    height: 100%;
}
</style>
