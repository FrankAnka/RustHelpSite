<script>
	import { text } from "@sveltejs/kit";

let CurrentCategory=0
let ItemList=[
/* Buildings(decay is in hours) */
[
/* Wood */
    {name:"Wood Wall",grade:"Wood",type:"Wall",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall.webp"},
    {name:"Wood Foundation",grade:"Wood",type:"Foundation",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-foundation.webp"},
    {name:"Wood Triangle Foundation",grade:"Wood",type:"TriangleFoundation",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-foundation-triangle.webp"},
    {name:"Wood Floor",grade:"Wood",type:"Floor",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor.webp"},
    {name:"Wood FloorTriangle",grade:"Wood",type:"Floor",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-triangle.webp"},
    {name:"Wood Window",grade:"wood",type:"WindowFrame",buildcost:140,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-window.webp"},
    {name:"Wood HalfWall",grade:"wood",type:"HalfWall",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-half.webp"},
    {name:"Wood LowWall",grade:"wood",type:"LowWall",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-low.webp"},
    {name:"Wood Doorway",grade:"Wood",type:"Frame",buildcost:140,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-doorway.webp"},
    {name:"Wood WallFrame",grade:"Wood",type:"Frame",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-frame.webp"},
    {name:"Wood FloorFrame",grade:"Wood",type:"Frame",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-frame.webp"},
    {name:"Wood Triangle FloorFrame",grade:"Wood",type:"Frame",buildcost:50,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-triangle-frame.webp"},
    {name:"Wood Roof",grade:"Wood",type:"Roof",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-roof.webp"},
    {name:"Wood RoofTriangle",grade:"Wood",type:"Roof",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-roof-triangle.webp"},
/* Stone */  
    {name:"Stone Wall",grade:"Stone",type:"Wall",buildcost:300,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall.webp"},
    {name:"Stone Foundation",grade:"Stone",type:"Foundation",buildcost:300,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-foundation.webp"},
    {name:"Stone Triangle Foundation",grade:"Stone",type:"TriangleFoundation",buildcost:150,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-foundation-triangle.webp"},
    {name:"Stone Floor",grade:"Stone",type:"Floor",buildcost:150,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor.webp"},
    {name:"Stone FloorTriangle",grade:"Stone",type:"Floor",buildcost:75,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor-triangle.webp"},
    {name:"Stone Window",grade:"Stone",type:"WindowFrame",buildcost:210,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-window.webp"},
    {name:"Stone HalfWall",grade:"Stone",type:"HalfWall",buildcost:300,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-half.webp"},
    {name:"Stone LowWall",grade:"Stone",type:"LowWall",buildcost:150,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-low.webp"},
    {name:"Stone Doorway",grade:"Stone",type:"Frame",buildcost:210,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-doorway.webp"},
    {name:"Stone WallFrame",grade:"Stone",type:"Frame",buildcost:150,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-wall-frame.webp"},
    {name:"Stone FloorFrame",grade:"Stone",type:"Frame",buildcost:150,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor-frame.webp"},
    {name:"Stone Triangle FloorFrame",grade:"Stone",type:"Frame",buildcost:75,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-floor-triangle-frame.webp"},
    {name:"Stone Roof",grade:"Stone",type:"Roof",buildcost:150,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-roof.webp"},
    {name:"Stone RoofTriangle",grade:"Stone",type:"Roof",buildcost:150,hp:500,decay:5,img:"https://cdn.rusthelp.com/images/256/stone-roof-triangle.webp"},
/* Metal */
    {name:"Metal Wall",grade:"Metal",type:"Wall",buildcost:200,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall.webp"},
    {name:"Metal Foundation",grade:"Metal",type:"Foundation",buildcost:200,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-foundation.webp"},
    {name:"Metal Triangle Foundation",grade:"Metal",type:"TriangleFoundation",buildcost:100,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-foundation-triangle.webp"},
    {name:"Metal Floor",grade:"Metal",type:"Floor",buildcost:100,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor.webp"},
    {name:"Metal FloorTriangle",grade:"Metal",type:"Floor",buildcost:50,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor-triangle.webp"},
    {name:"Metal Window",grade:"Metal",type:"WindowFrame",buildcost:140,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-window.webp"},
    {name:"Metal HalfWall",grade:"Metal",type:"HalfWall",buildcost:200,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-half.webp"},
    {name:"Metal LowWall",grade:"Metal",type:"LowWall",buildcost:100,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-low.webp"},
    {name:"Metal Doorway",grade:"Metal",type:"Frame",buildcost:140,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-doorway.webp"},
    {name:"Metal WallFrame",grade:"Metal",type:"Frame",buildcost:100,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-wall-frame.webp"},
    {name:"Metal FloorFrame",grade:"Metal",type:"Frame",buildcost:100,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor-frame.webp"},
    {name:"Metal Triangle FloorFrame",grade:"Metal",type:"Frame",buildcost:50,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-floor-triangle-frame.webp"},
    {name:"Metal Roof",grade:"Metal",type:"Roof",buildcost:100,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-roof.webp"},
    {name:"Metal RoofTriangle",grade:"Metal",type:"Roof",buildcost:100,hp:1000,decay:8,img:"https://cdn.rusthelp.com/images/256/metal-roof-triangle.webp"},
/* Armored */
    {name:"Armored Wall",grade:"Armored",type:"Wall",buildcost:25,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall.webp"},
    {name:"Armored Foundation",grade:"Armored",type:"Foundation",buildcost:25,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-foundation.webp"},
    {name:"Armored Triangle Foundation",grade:"Armored",type:"TriangleFoundation",buildcost:13,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-foundation-triangle.webp"},
    {name:"Armored Floor",grade:"Armored",type:"Floor",buildcost:13,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor.webp"},
    {name:"Armored FloorTriangle",grade:"Armored",type:"Floor",buildcost:7,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor-triangle.webp"},
    {name:"Armored Window",grade:"Armored",type:"WindowFrame",buildcost:18,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-window.webp"},
    {name:"Armored HalfWall",grade:"Armored",type:"HalfWall",buildcost:25,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-half.webp"},
    {name:"Armored LowWall",grade:"Armored",type:"LowWall",buildcost:13,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-low.webp"},
    {name:"Armored Doorway",grade:"Armored",type:"Frame",buildcost:18,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-doorway.webp"},
    {name:"Armored WallFrame",grade:"Armored",type:"Frame",buildcost:13,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-wall-frame.webp"},
    {name:"Armored FloorFrame",grade:"Armored",type:"Frame",buildcost:13,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor-frame.webp"},
    {name:"Armored Triangle FloorFrame",grade:"Armored",type:"Frame",buildcost:7,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-floor-triangle-frame.webp"},
    {name:"Armored Roof",grade:"Armored",type:"Roof",buildcost:13,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-roof.webp"},
    {name:"Armored RoofTriangle",grade:"Armored",type:"Roof",buildcost:13,hp:2000,decay:12,img:"https://cdn.rusthelp.com/images/256/armored-roof-triangle.webp"},
/* Doors */
    {name:"Wood Door",grade:"Wood",type:"Door",buildcost:300,hp:200,decay:3,img:"https://cdn.rusthelp.com/images/256/door-hinged-wood.webp"},
    {name:"Wood Double Door",grade:"Wood",type:"Door",buildcost:350,hp:200,decay:3,img:"https://cdn.rusthelp.com/images/256/door-double-hinged-wood.webp"},
    {name:"Sheet Metal Door",grade:"Metal",type:"Door",buildcost:150,hp:250,decay:8,img:"https://cdn.rusthelp.com/images/256/door-hinged-metal.webp"},
    {name:"Sheet Metal Double Door",grade:"Metal",type:"Door",buildcost:200,hp:250,decay:8,img:"https://cdn.rusthelp.com/images/256/door-double-hinged-metal.webp"},
    {name:"Armored Door",grade:"Armored",type:"Door",buildcost:"20 hqm and 5 gears",hp:1000,decay:12,img:"https://cdn.rusthelp.com/images/256/door-hinged-toptier.webp"},
    {name:"Armored Double Door",grade:"Armored",type:"Door",buildcost:"25 hqm and 5 gears",hp:1000,decay:12,img:"https://cdn.rusthelp.com/images/256/door-double-hinged-toptier.webp"},
    {name:"Garage Door",grade:"Metal",type:"Door",buildcost:"300 metal 2 gears",hp:600,decay:8,img:"https://cdn.rusthelp.com/images/256/wall-frame-garagedoor.webp"},
    {name:"Ladder Hatch",grade:"Metal",type:"Door",buildcost:"1 ladder 300 metal 3 gears",hp:250,decay:8,img:"https://cdn.rusthelp.com/images/256/floor-ladder-hatch.webp"},
    {name:"Triangle Ladder Hatch",grade:"Metal",type:"Door",buildcost:"1 ladder 300 metal 3 gears",hp:250,decay:8,img:"https://cdn.rusthelp.com/images/256/floor-triangle-ladder-hatch.webp"},

/* Windows */

],
/* Weapons */
[



],
/* Explosives */
[


],
/* Clothes */
[   


],
/* Food/Meds */
[


]
]
</script>


<section class="ScrollableGrid">
        {#each ItemList[0] as Item}
            <button class="Item">
                <div style="width: 90%; height:80%;" >
                <img src={Item.img} alt=Item.name>
                </div>
                <h2 style="width: 60%; text-align:center; margin-left:15%;">{Item.name}</h2>
            </button>
        {/each}
</section>




<style>
.ScrollableGrid{
    display: grid;
    position: absolute;
    overflow-y: scroll;
    overflow-x: hidden;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
    row-gap: 8%;
    grid-template-rows: repeat(20 , 1fr);
    border: 3px solid #717171;
    border-radius: 10px;
    width: 70%;
    height: 80%;
    top: 15%;
    left: 15%;
    padding: 2%;

}
.Item  {
    display: flex;
    justify-self:center;
    justify-content: center;
    border: #717171 solid 1px;
    border-radius: 10px;
    flex-direction: column;
    width: 80%;
    height: 100%;
    padding: 1%;


}
</style>