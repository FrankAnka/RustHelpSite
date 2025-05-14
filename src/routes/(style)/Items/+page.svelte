<script>

let CurrentCategory=0
let searchString=""
let searchResults = []
let hp
let decay
let buildcost
let grade
let res /*resistance*/
let ObtainVisiblity = "none"

/* Explosives */
let damage
let totalSulfur
let splashRadius
let craftCost
let tier

let itemname
let local /*location*/
let dropRate
let img
let popupDisplay="none"
let scrollGridColumns=5
let ItemList=[

/* Buildings(decay is in hours) */
[
/* Wood */
    {name:"Wood Wall",grade:"Wood",type:"Wall",buildcost:200,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall.webp"},
    {name:"Wood Foundation",grade:"Wood",type:"Foundation",buildcost:200,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-foundation.webp"},
    {name:"Wood Triangle Foundation",grade:"Wood",type:"TriangleFoundation",buildcost:100,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-foundation-triangle.webp"},
    {name:"Wood Floor",grade:"Wood",type:"Floor",buildcost:200,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor.webp"},
    {name:"Wood FloorTriangle",grade:"Wood",type:"Floor",buildcost:200,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-triangle.webp"},
    {name:"Wood Window",grade:"wood",type:"WindowFrame",buildcost:140,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-window.webp"},
    {name:"Wood HalfWall",grade:"wood",type:"HalfWall",buildcost:200,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-half.webp"},
    {name:"Wood LowWall",grade:"wood",type:"LowWall",buildcost:100,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-low.webp"},
    {name:"Wood Doorway",grade:"Wood",type:"Frame",buildcost:140,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-doorway.webp"},
    {name:"Wood WallFrame",grade:"Wood",type:"Frame",buildcost:100,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-frame.webp"},
    {name:"Wood FloorFrame",grade:"Wood",type:"Frame",buildcost:100,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-frame.webp"},
    {name:"Wood Triangle FloorFrame",grade:"Wood",type:"Frame",buildcost:50,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-triangle-frame.webp"},
    {name:"Wood Roof",grade:"Wood",type:"Roof",buildcost:200,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-roof.webp"},
    {name:"Wood RoofTriangle",grade:"Wood",type:"Roof",buildcost:200,hp:250,res:0.9,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-roof-triangle.webp"},
/* Stone */  
    {name:"Stone Wall",grade:"Stone",type:"Wall",buildcost:300,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall.webp"},
    {name:"Stone Foundation",grade:"Stone",type:"Foundation",buildcost:300,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-foundation.webp"},
    {name:"Stone Triangle Foundation",grade:"Stone",type:"TriangleFoundation",buildcost:150,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-foundation-triangle.webp"},
    {name:"Stone Floor",grade:"Stone",type:"Floor",buildcost:150,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor.webp"},
    {name:"Stone FloorTriangle",grade:"Stone",type:"Floor",buildcost:75,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor-triangle.webp"},
    {name:"Stone Window",grade:"Stone",type:"WindowFrame",buildcost:210,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-window.webp"},
    {name:"Stone HalfWall",grade:"Stone",type:"HalfWall",buildcost:300,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-half.webp"},
    {name:"Stone LowWall",grade:"Stone",type:"LowWall",buildcost:150,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-low.webp"},
    {name:"Stone Doorway",grade:"Stone",type:"Frame",buildcost:210,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-doorway.webp"},
    {name:"Stone WallFrame",grade:"Stone",type:"Frame",buildcost:150,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-frame.webp"},
    {name:"Stone FloorFrame",grade:"Stone",type:"Frame",buildcost:150,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor-frame.webp"},
    {name:"Stone Triangle FloorFrame",grade:"Stone",type:"Frame",buildcost:75,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor-triangle-frame.webp"},
    {name:"Stone Roof",grade:"Stone",type:"Roof",buildcost:150,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-roof.webp"},
    {name:"Stone RoofTriangle",grade:"Stone",type:"Roof",buildcost:150,hp:500,res:0.5,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-roof-triangle.webp"},
/* Metal */
    {name:"Metal Wall",grade:"Metal",type:"Wall",buildcost:200,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall.webp"},
    {name:"Metal Foundation",grade:"Metal",type:"Foundation",buildcost:200,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-foundation.webp"},
    {name:"Metal Triangle Foundation",grade:"Metal",type:"TriangleFoundation",buildcost:100,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-foundation-triangle.webp"},
    {name:"Metal Floor",grade:"Metal",type:"Floor",buildcost:100,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor.webp"},
    {name:"Metal FloorTriangle",grade:"Metal",type:"Floor",buildcost:50,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor-triangle.webp"},
    {name:"Metal Window",grade:"Metal",type:"WindowFrame",buildcost:140,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-window.webp"},
    {name:"Metal HalfWall",grade:"Metal",type:"HalfWall",buildcost:200,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-half.webp"},
    {name:"Metal LowWall",grade:"Metal",type:"LowWall",buildcost:100,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-low.webp"},
    {name:"Metal Doorway",grade:"Metal",type:"Frame",buildcost:140,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-doorway.webp"},
    {name:"Metal WallFrame",grade:"Metal",type:"Frame",buildcost:100,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-frame.webp"},
    {name:"Metal FloorFrame",grade:"Metal",type:"Frame",buildcost:100,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor-frame.webp"},
    {name:"Metal Triangle FloorFrame",grade:"Metal",type:"Frame",buildcost:50,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor-triangle-frame.webp"},
    {name:"Metal Roof",grade:"Metal",type:"Roof",buildcost:100,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-roof.webp"},
    {name:"Metal RoofTriangle",grade:"Metal",type:"Roof",buildcost:100,hp:1000,res:0.5,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-roof-triangle.webp"},
/* Armored */
    {name:"Armored Wall",grade:"Armored",type:"Wall",buildcost:25,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall.webp"},
    {name:"Armored Foundation",grade:"HQM",type:"Foundation",buildcost:25,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-foundation.webp"},
    {name:"Armored Triangle Foundation",grade:"HQM",type:"TriangleFoundation",buildcost:13,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-foundation-triangle.webp"},
    {name:"Armored Floor",grade:"HQM",type:"Floor",buildcost:13,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor.webp"},
    {name:"Armored FloorTriangle",grade:"HQM",type:"Floor",buildcost:7,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor-triangle.webp"},
    {name:"Armored Window",grade:"HQM",type:"WindowFrame",buildcost:18,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-window.webp"},
    {name:"Armored HalfWall",grade:"HQM",type:"HalfWall",buildcost:25,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-half.webp"},
    {name:"Armored LowWall",grade:"HQM",type:"LowWall",buildcost:13,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-low.webp"},
    {name:"Armored Doorway",grade:"HQM",type:"Frame",buildcost:18,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-doorway.webp"},
    {name:"Armored WallFrame",grade:"HQM",type:"Frame",buildcost:13,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-frame.webp"},
    {name:"Armored FloorFrame",grade:"HQM",type:"Frame",buildcost:13,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor-frame.webp"},
    {name:"Armored Triangle FloorFrame",grade:"HQM",type:"Frame",buildcost:7,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor-triangle-frame.webp"},
    {name:"Armored Roof",grade:"HQM",type:"Roof",buildcost:13,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-roof.webp"},
    {name:"Armored RoofTriangle",grade:"HQM",type:"Roof",buildcost:13,hp:2000,res:0.5,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-roof-triangle.webp"},
/* Doors */
    {name:"Wood Door",grade:"Wood",type:"Door",buildcost:300,hp:200,res:2,decay:3,img:"https://cdn.rusthelp.com/images/256/door-hinged-wood.webp"},
    {name:"Wood Double Door",grade:"Wood",type:"Door",buildcost:350,hp:200,res:2,decay:3,img:"https://cdn.rusthelp.com/images/256/door-double-hinged-wood.webp"},
    {name:"Sheet Metal Door",grade:"Metal",type:"Door",buildcost:150,hp:250,res:0.8,decay:8,img:"https://cdn.rusthelp.com/images/256/door-hinged-metal.webp"},
    {name:"Sheet Metal Double Door",grade:"Metal",type:"Door",buildcost:200,hp:250,res:0.8,decay:8,img:"https://cdn.rusthelp.com/images/256/door-double-hinged-metal.webp"},
    {name:"Armored Door",type:"Door",buildcost:"20 hqm and 5 gears",hp:1000,res:0.8,decay:12,img:"https://cdn.rusthelp.com/images/256/door-hinged-toptier.webp"},
    {name:"Armored Double Door",type:"Door",buildcost:"25 hqm and 5 gears",hp:1000,res:0.8,decay:12,img:"https://cdn.rusthelp.com/images/256/door-double-hinged-toptier.webp"},
    {name:"Garage Door",type:"Door",buildcost:"300 metal 2 gears",hp:600,res:0.8,decay:8,img:"https://cdn.rusthelp.com/images/256/wall-frame-garagedoor.webp"},
    {name:"Ladder Hatch",type:"Door",buildcost:"1 ladder 300 metal 3 gears",hp:250,res:0.8,decay:8,img:"https://cdn.rusthelp.com/images/256/floor-ladder-hatch.webp"},
    {name:"Triangle Ladder Hatch",type:"Door",buildcost:"1 ladder 300 metal 3 gears",hp:250,res:0.8,decay:8,img:"https://cdn.rusthelp.com/images/256/floor-triangle-ladder-hatch.webp"},

/* Windows */

],

/* Explosives */
[
  {
    name: "Rocket",
    craftCost: {
      MetalPipe: 2,
      Gunpowder: 150,
      Explosives: 10
    },
    totalSulfur: 1400,
    damage: 275,
    splashRadius: 3.8,
    img: "https://wiki.rustclash.com/img/items180/ammo.rocket.basic.png",
    tier: 3,
    dropRate: ["25%", "5.56%"],
    location: ["Helicopter Crate", "Locked Crate"]
  },
  {
    name: "Timed Explosive Charge (C4)",
    craftCost: {
      Explosives: 20,
      Cloth: 5,
      TechTrash: 2
    },
    totalSulfur: 2000,
    damage: 550,
    splashRadius: 4,
    img: "https://wiki.rustclash.com/img/items180/explosive.timed.png",
    tier: 3,
    dropRate: ["34.39%", "25%", "13%","26.53%"],
    location: ["APC Crate (Bradley)", "Helicopter Crate", "Locked Crate","Supply Drop"]
  },
  {
    name: "Satchel Charge",
    craftCost: {
      BeancanGrenade: 4,
      SmallStash: 1,
      Rope: 1
    },
    totalSulfur: 480,
    damage: 75,
    splashRadius: 4,
    img: "https://wiki.rustclash.com/img/items180/explosive.satchel.png",
    tier: 1,
    dropRate: ["48.9%", "0.44%", "1.1%", "0.44%", "0.44%"],
    location: [
      "Supply Drop",
      "Crate",
      "Sunken Chest",
      "Underwater Lab Blue Crate",
      "Wagon Crate"
    ]
  },
  {
    name: "Beancan Grenade",
    craftCost: {
      Gunpowder: 60,
      MetalFragments: 20
    },
    totalSulfur: 120,
    damage: 15,
    splashRadius: 1.5,
    img: "https://wiki.rustclash.com/img/items180/grenade.beancan.png",
    tier: 1,
    dropRate: ["1.49%", "1.49%", "1.49%", "0.44%", "1.1%"],
    location: [
      "Elite Tier Crate",
      "Heavy Scientist",
      "Underwater Lab Elite Crate",
      "Crate",
      "Sunken Chest"
    ]
  },
  {
    name: "Explosive 5.56 Rifle Ammo",
    craftCost: {
      MetalFragments: 10,
      Gunpowder: 20,
      Sulfur: 10
    },
    totalSulfur: 50,
    damage: 5,
    splashRadius: 0.5,
    img: "https://wiki.rustclash.com/img/items180/ammo.rifle.explosive.png",
    tier: 3,
    dropRate: ["19%", "15%", "12.61%", "6.52%", "5.56%"],
    location: [
      "APC Crate (Bradley)",
      "Helicopter Crate",
      "Supply Drop",
      "Underwater Lab Ammo Crate",
      "Locked Crate"
    ]
  },
  {
    name: "Propane Explosive Bomb",
    craftCost: {
      MetalFragments: 160,
      Scrap: 10,
      Charcoal: 1350,
      Sulfur: 960,
      AnimalFat: 15,
      Cloth: 5
    },
    totalSulfur: 960,
    damage: 150.5,
    splashRadius: 5.2,
    img: "https://wiki.rustclash.com/img/items180/catapult.ammo.explosive.png",
    tier: 2,
    dropRate: ["Unlock through tech tree"],
    location: ["None"]
  },
  {
    name: "MLRS Rocket",
    craftCost: null,
    totalSulfur: null,
    damage: 350,
    splashRadius: 10,
    img: "https://wiki.rustclash.com/img/items180/ammo.rocket.mlrs.png",
    tier: "military",
    dropRate: ["100%", "15%", "50%"],
    location: ["APC Crate (Bradley)", "Helicopter Crate", "Elite Crate"]
  },
  {
    name: "40mm HE Grenade",
    craftCost: null,
    totalSulfur: null,
    damage: 35.3,
    splashRadius: 3.5,
    img: "https://wiki.rustclash.com/img/items180/ammo.grenadelauncher.he.png",
    tier: "military",
    dropRate: ["14%", "14%", "14%"],
    location: [
      "Heavy Scientist",
      "Heavy Scientist With Minigun",
      "Heavy Scientist With Flamethrower"
    ]
  }
]


]


function searchItem(searchString){
    console.log("Searching for: " + searchString);
    let searchResults = ItemList[CurrentCategory].filter(item => item.name.toLowerCase().includes(searchString.toLowerCase()));
    
    return searchResults;

}

/* Also handle recent searches */
function InfoPopup(Item) {
    popupDisplay = "flex";
    let i = 0;

    if (i <= 2) {
        i++;
        localStorage.setItem("Recent" + i, JSON.stringify(Item));
    }
    if (i === 3) { // Fix the assignment issue here
        i = 1;
        localStorage.setItem("Recent" + i, JSON.stringify(Item));
    }

    // Handle data based on the current category
    if (CurrentCategory === 0) {
        hp = Item.hp;
        decay = Item.decay;
        buildcost = Item.buildcost;
        grade = Item.grade;
        itemname = Item.name;
        img = Item.img;
        res=Item.res;
    } else if (CurrentCategory === 1) {
        damage = Item.damage;
        splashRadius = Item.splashRadius;
        totalSulfur = Item.totalSulfur;
        craftCost = Item.craftCost || {}; // Ensure craftCost is set
        grade = Item.grade;
        itemname = Item.name;
        img = Item.img;
        tier=Item.tier;
        local=Item.location;
        dropRate=Item.dropRate;
    }
}

</script>

<svg width="100vw" height="100%" style="position:absolute;opacity:0,5; z-index:1;top:0; left:0; display:{popupDisplay};">
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <rect width="100%" height="100%" style="fill=#000000;" on:click={()=>popupDisplay="none"}></rect>
</svg>
    <rect width="100%" height="100%" filter="url(#noise)" fill="#000000"></rect>

    <div class="join">
        <div>
          <div>
            <input class="input join-item" style="position: absolute;top : 10%;left: 15%; width:15% " bind:value={searchString} placeholder="Search" />
          </div>
        </div>
      </div>

      <div class="join join-vertical lg:join-horizontal" style="position: absolute; top : 10%;left: 30%; width:15% ">
        <button class="btn join-item"on:click={()=>CurrentCategory=0}>Buildings</button>
        <button class="btn join-item"on:click={()=>CurrentCategory=1}>Explosives</button>

      </div>

<section id="grid" class="ScrollableGrid no-scrollbar" style="grid-template-columns:repeat({scrollGridColumns}, 1fr) ;">
    {#if searchString.length >0}
        {#each searchItem(searchString) as Item}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div class="card bg-base-100 w-80 shadow-sm" on:click={()=>InfoPopup(Item)}>
            <div class="card-body">
            <h2 class="card-title">{Item.name}</h2>
            </div>
            <figure>
            <img
                src={Item.img}
                alt="{Item.name}" />
            </figure>
        </div>
    
        {/each}
    {:else}
        {#each ItemList[CurrentCategory] as Item}

        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div class="card bg-base-100 w-95 shadow-sm" on:click={()=>InfoPopup(Item)}>
            <div class="card-body">
            <h2 class="card-title">{Item.name}</h2>
            </div>
            <figure>
            <img
                src={Item.img}
                alt="{Item.name}" />
            </figure>
        </div>
        {/each}
    {/if}
</section>

<div style="display: {popupDisplay}; font-family:'Times New Roman', Times, serif;margin: 0;padding: 0;" class="InfoPopup">

  {#if CurrentCategory === 0}
    <h1 style="font-size: 40px; position:absolute; top:8%; left:5%;">{itemname}</h1>
    <img style="position: absolute; top:16%; left:5%; border: #717171 2px solid; border-radius:20px;" src={img} alt={itemname}>


      <div class="stats stats-vertical shadow no-scrollbar" style="overflow-y: scroll; position: absolute; top: 50%; left: 5%; width: 22%; height: 30%; border-radius: 20px; border: #717171 solid 2px; background-color: #1f1c2b;">
        <div class="stat">
          <div class="stat-title">Health</div>
          <div class="stat-value">{hp}</div>
        </div>
      
        <div class="stat">
          <div class="stat-title">Decay (hours)</div>
          <div class="stat-value">{decay}</div>
        </div>
      
        <div class="stat">
          <div class="stat-title">Buildcost</div>
          <div class="stat-value">{buildcost} {grade||""}</div>
        </div>
      </div>

      <div class="overflow-x-auto" style="position: absolute; left: 33%; top:16%; border-radius: 20px; border: #717171 solid 2px; background-color: #1f1c2b;">
        <table class="table">
          <!-- head -->
          <thead>
            <tr>
              <th>Item</th>
              <th>Damage</th>
              <th>Quantity</th>
              <th>Total sulfur</th>
            </tr>
          </thead>
          <tbody>
            {#each ItemList[1] as item}
            <tr class="hover:bg-base-300">
              <th>{item.name}</th>   
              <td>{item.damage*res}</td>
              <td>{Math.ceil(hp/(item.damage*res))}</td>
              <td>{item.totalSulfur*Math.ceil(hp/(item.damage*res))}</td>
            </tr>
            {/each}
          </tbody>
        </table>
      </div>




  {:else if CurrentCategory === 1}
    <h1 style="font-size: 40px; position:absolute; top:8%; left:5%;">{itemname}</h1>
    <img style="position: absolute; top:20%; left:8%; border: #717171 2px solid; border-radius:20px;transform:scale(1.4);" src={img} alt={itemname}>
    <div class="stats stats-vertical shadow" style=" overflow-y:hidden;position: absolute; top: 50%; left: 5%; width: 22%; height: 30%; border-radius: 20px; border: #717171 solid 2px; background-color: #1f1c2b;">
        <div class="stat">
          <div class="stat-title">Damage</div>
          <div class="stat-value">{damage}</div>
        </div>
      
        <div class="stat">
          <div class="stat-title">Splash Radius(meters)</div>
          <div class="stat-value">{splashRadius}</div>
        </div>
      
        <div class="stat">
          <div class="stat-title">Total Sulfur cost</div>
          <div class="stat-value">{totalSulfur}</div>
        </div>
        
      </div>
      <button class="btn btn-xl btn-accent" style="position: absolute;top:80%;left:10%;" on:click={() => ObtainVisiblity = ObtainVisiblity === "none" ? "block" : "none"}>Obtaining</button>
      <div style="position: absolute; z-index: 10; top: 13%; left: 58%;">
        <!-- svelte-ignore empty-block -->
        {#if tier==="military"}
        <h2 style="font-size:20px; justify-self:center;">Military tier</h2>
        {:else}
        <h2 style="font-size:20px; justify-self:center;">Tier {tier}</h2>
        {/if}
        
      </div>
      
    <table class="table" style="position:absolute;top: 50%;left:30%;width:auto;height:28%;border-radius: 20px; background-color: #1f1c2b;display:{ObtainVisiblity};z-index: 10;">
        <!-- head -->
        <thead>
            <tr>
                <th>Source</th>
                <th>Droprate</th>
            </tr>
        </thead>
        <tbody>
            {#each (local || []) as loc, index}
                <tr class="hover:bg-base-300">
                    <th>{loc}</th>
                    <td>{dropRate?.[index] || "N/A"}</td>
                </tr>
            {/each}
        </tbody>
    </table>


    <section class="MoreInfo">
        {#if craftCost && Object.keys(craftCost).length > 0}
        
            <div  style="width: 100%;">
              <h2 style="font-size:20px; justify-self:center;">Crafting</h2>
              <table class="table">
                <!-- head -->
                
                <thead>
                  <tr>
                    <th>Item</th>
                    <th>Amount</th>
                  </tr>
                </thead>
                <tbody>
                  <!-- row 1 -->
                  {#each Object.entries(craftCost) as [material, amount]}
                  <tr>
                    
                    <td>{material}</td>
                    <td>{amount}</td>
                    
                  </tr>
                  {/each}
                </tbody>
                
              </table>
            </div>
        {:else}
            <h3 style="font-size:18px; justify-self:center;">Item cannot be crafted</h3>
        {/if}
    </section>
  {/if}
</div>




<style>
    :global(body){
        overflow: hidden;
        margin: 0;
        padding: 0;
        height: 100%;
        width: 100%;
    }
.ScrollableGrid{
    display: grid;
    position: absolute;
    overflow-y: scroll;
    overflow-x: hidden;
    row-gap: 8%;
    column-gap: 2%;
    grid-template-rows: repeat(auto-fill, 1fr);
    border: 3px solid #717171;
    border-radius: 10px;
    justify-items: center;
    width: 70%;
    height: 80%;
    top: 15%;
    left: 15%;
    padding: 2%;

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
.MoreInfo{
    display: grid;
    grid-template-columns: repeat(auto-fill, 1fr);
    grid-template-rows: repeat(auto-fill, 1fr);
    position: absolute;
    top: 16%;
    left: 30%;
    width: 60%;
    height: 64%;
    border-radius: 20px;
    background-color: #1f1c2b;
  
}
h1,h2,h3{
    color: #ffffff;
    font-family:'Times New Roman', Times, serif;
    text-align: center;
    margin: 0;
    padding: 0;
    
}

.no-scrollbar {
    scrollbar-width: none; /* For Firefox */
}

.no-scrollbar::-webkit-scrollbar {
    display: none; /* For Chrome, Edge, and Safari */
}
</style>