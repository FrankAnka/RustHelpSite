<script>
let popupDisplay = "none";
let video
let Loot
let Name
let img

let Monuments = [
 [ // No keycard required
  {
    name: "Abandoned Cabins",
    img: "Abondoned cabins.webp",
    vid: "",
    Loot: {
      crates: {
        "Basic Crate": 2,
        "Food Crate": 2,
        "Barrel": 4
      },
      cards: [],
      diesel: false
    }
  },
  {
    name: "Dome",
    img: "Dome.jpg",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 3,
        "Basic Crate": 4,
        "Food Crate": 2
      },
      cards: [],
      diesel: false
    }
  },
  {
    name: "Ferry Terminal",
    img: "ferry.jpg",
    vid: "",
    Loot: {
      crates: {
        "Basic Crate": 4,
        "Food Crate": 3,
        "Barrel": 5
      },
      cards: ["Green Card"],
      diesel: false
    }
  },
  {
    name: "Junkyard",
    img: "junkyard.jpg",
    vid: "",
    Loot: {
      crates: {
        "Basic Crate": 4,
        "Food Crate": 2,
        "Barrel": 6
      },
      cards: ["Green Card"],
      diesel: false
    }
  },
  {
    name: "Lighthouse",
    img: "lighthouse.jpg",
    vid: "",
    Loot: {
      crates: {
        "Basic Crate": 3,
        "Food Crate": 2,
        "Barrel": 4
      },
      cards: ["Green Card"],
      diesel: false
    }
  },
  {
    name: "Mining Outpost",
    img: "mining-outpost.jpg",
    vid: "",
    Loot: {
      crates: {
        "Basic Crate": 2,
        "Food Crate": 1,
        "Barrel": 4
      },
      cards: [""],
      diesel: false
    }
  },
  {
    name: "Oxum's Gas Station",
    img: "Oxums.jpg",
    vid: "",
    Loot: {
      crates: {
        "Basic Crate": 2,
        "Food Crate": 2,
        "Barrel": 4
      },
      cards: ["Green Card"],
      diesel: false
    }
  },
  {
    name: "Supermarket",
    img: "supermarket.jpg",
    vid: "",
    Loot: {
      crates: {
        "Basic Crate": 2,
        "Food Crate": 3,
        "Barrel": 4
      },
      cards: ["Green Card"],
      diesel: false
    }
  },
  {
    name: "Abandoned Military Base",
    img: "Abandonded-Military-Base.jpg",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 3,
        "Basic Crate": 3,
        "Barrel": 6
      },
      cards: [],
      diesel: false
    }
  },
  {
    name: "Jungle Ziggurat",
    img: "jungle ziggurat.jpg",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 2,
        "Basic Crate": 3,
        "Barrel": 4
      },
      cards: [],
      diesel: false
    }
  }
],
  [ // Green keycard required
  {
    name: "Harbor",
    img: "harbor.jpg",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 1,
        "Basic Crate": 3,
        "Food Crate": 2,
        "Barrel": 4
      },
      cards: ["Blue Card"],
      diesel: false
    }
  },
  {
    name: "Satellite Dish ",
    img: "Satallite-Dish.jpg",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 1,
        "Basic Crate": 3,
        "Food Crate": 1,
        "Barrel": 4
      },
      cards: ["Blue Card"],
      diesel: false
    }
  },
  {
    name: "Sewer Branch",
    img: "Sewer-Branch-Monument.jpg",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 1,
        "Basic Crate": 3,
        "Food Crate": 2,
        "Barrel": 4
      },
      cards: ["Blue Card"],
      diesel: false
    }
  }
]
,
  [ // Blue keycard required
  {
    name: "Airfield",
    img: "airfield.png",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 4,
        "Basic Crate": 4,
        "Food Crate": 3,
        "Barrel": 6
      },
      cards: ["Red Card"],
      diesel: false
    }
  },
  {
    name: "Power Plant",
    img: "Power_Plant.webp",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 4,
        "Basic Crate": 4,
        "Food Crate": 2,
        "Barrel": 6
      },
      cards: ["Red Card","Green Card"],
      diesel: true
    }
  },
  {
    name: "Train Yard",
    img: "trainyard.png",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 4,
        "Basic Crate": 4,
        "Food Crate": 2,
        "Barrel": 6
      },
      cards: ["Red Card"],
      diesel: true
    }
  },
  {
    name: "Water Treatment Plant",
    img: "watertreat.avif",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 3,
        "Basic Crate": 4,
        "Food Crate": 2,
        "Barrel": 6
      },
      cards: ["Red Card"],
      diesel: true
    }
  },
  {
    name: "Nuclear Missile Silo",
    img: "missile silo.jpg",
    vid: "",
    Loot: {
      crates: {
        "Elite Crate": 2,
        "Military Crate": 2,
        "Basic Crate": 2,
        "Food Crate": 1
      },
      cards: ["Red Card"],
      diesel: false
    }
  },
  {
    name: "Arctic Research Base",
    img: "arcticbase.jpg",
    vid: "",
    Loot: {
      crates: {
        "Military Crate": 2,
        "Basic Crate": 3,
        "Food Crate": 2,
        "Barrel": 5
      },
      cards: ["Red Card"],
      diesel: false
    }
  }
],
  [ // Red keycard required
    {
      name: "Cargo Ship",
      img: "cargo.webp",
      vid: "",
      Loot: {
        crates: {
          "Elite Crate": 3,
          "Military Crate": 4,
          "Basic Crate": 4,
          "Barrel": 6,
          "Locked Crate": 4
        },
        cards: [],
        diesel: false
      }
    },
    {
      name: "Large Oil Rig",
      img: "Loil.jpg",
      vid: "",
      Loot: {
        crates: {
          "Elite Crate": 3,
          "Military Crate": 4,
          "Basic Crate": 4,
          "Barrel": 6,
          "Locked Crate": 1
        },
        cards: [],
        diesel: true
      }
    },
    {
      name: "Launch Site",
      img: "launch.webp",
      vid: "",
      Loot: {
        crates: {
          "Elite Crate": 4,
          "Military Crate": 12,
          "Basic Crate": 4,
          "Food Crate": 20,
          "Barrel": 6
        },
        cards: [],
        diesel: false
      }
    },
    {
      name: "Military Tunnel",
      img: "tunnels.jpg",
      vid: "",
      Loot: {
        crates: {
          "Elite Crate": 10,
          "Military Crate": 4,
          "Basic Crate": 4,
          "Food Crate": 14,
          "Barrel": 6
        },
        cards: [],
        diesel: false
      }
    },
    {
      name: "Small Oil Rig",
      img: "smoil.png",
      vid: "",
      Loot: {
        crates: {
          "Elite Crate": 2,
          "Military Crate": 3,
          "Basic Crate": 3,
          "Barrel": 6,
          "Locked Crate": 1
        },
        cards: [],
        diesel: true
      }
    },
    {
      name: "Underwater Lab",
      img: "labs.jpg",
      vid: "",
      Loot: {
        crates: {
          "Elite Crate": 2,
          "Military Crate": 4,
          "Basic Crate": 4,
          "Barrel": 6
        },
        cards: [],
        diesel: false
      }
    },
    {
      name: "Giant Excavator Pit",
      img: "excav.webp",
      vid: "",
      Loot: {
        crates: {
          "Military Crate": 1,
          "Basic Crate": 1,
          "Food Crate": 8,
          "Barrel": 6
        },
        cards: [],
        diesel: true
      }
    }
  ]
];


function Vidpopup(x){
popupDisplay="block"
video = x.vid
Name = x.name
Loot =x.Loot
img=x.img
}
</script>

<svg width="100vw" height="200%" style="position:absolute;opacity:0,5; z-index:1;top:0; left:0; display:{popupDisplay};">
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
        
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
    <img src={monument.img} alt={monument.name} on:click={()=>Vidpopup(monument)} />
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
        
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
        <img src={monument.img} alt={monument.name} on:click={()=>Vidpopup(monument)}/>
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
        
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
        <img src={monument.img} alt={monument.name} on:click={()=>Vidpopup(monument)} />
    </div>
    {/each}

</div>

<div style="display: {popupDisplay}; font-family:'Times New Roman', Times, serif;margin: 0;padding: 0; background-image:{img}" class="InfoPopup">
    <img src="{img}" alt="asdasdasdasd" style="z-index: -1;position:absolute; top:0%;left:1%; height:100%;width:100%;">
    <h1 style="color: black ; top:5%;position:absolute;left:46%;">{Name}</h1>

<div class="overflow-x-auto" style="position: absolute; top:15%;left:5%;width:25%;">
<table class="table">
    <!-- head -->
    <thead>
    <tr>
        <th>Type</th>
        <th>Amount</th>

    </tr>
    </thead>

    <tbody>
    <!-- row 1 -->
    {#if Loot}
    {#each Object.entries(Loot.crates) as [item,amount]}
    <tr>
        <td>{item}</td>
        <td>{amount}</td>


    
    </tr>
    {/each}

    {/if}
    </tbody>
</table>
</div>


    </div>




<style>

h1,h2{
    color: #ffffff;
    font-family:'Times New Roman', Times, serif;
    text-align: center;
    margin: 0;
    padding: 0;
    font-size: xx-large;
    
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
    background-size: cover;

    

}
img{
    height: 100%;
}
</style>
