<script>
	import { text } from "@sveltejs/kit";

let CurrentCategory=0
let ItemList=[
/* Buildings(decay is in hours) */
[
    {name:"WoodWall",grade:"Wood",type:"Wall",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall.webp"},
    {name:"WoodFoundation",grade:"Wood",type:"Foundation",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-foundation.webp"},
    {name:"WoodTriangleFoundation",grade:"Wood",type:"TriangleFoundation",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-foundation-triangle.webp"},
    {name:"WoodFloor",grade:"Wood",type:"Floor",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor.webp"},
    {name:"WoodFloorTriangle",grade:"Wood",type:"Floor",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-triangle.webp"},
    {name:"WoodWindow",grade:"wood",type:"WindowFrame",buildcost:140,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-window.webp"},
    {name:"WoodHalfWall",grade:"wood",type:"HalfWall",buildcost:200,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-half.webp"},
    {name:"WoodLowWall",grade:"wood",type:"LowWall",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-low.webp"},
    {name:"WoodDoorway",grade:"Wood",type:"Frame",buildcost:140,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-doorway.webp"},
    {name:"WoodWallFrame",grade:"Wood",type:"Frame",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-wall-frame.webp"},
    {name:"WoodFloorFrame",grade:"Wood",type:"Frame",buildcost:100,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-frame.webp"},
    {name:"WoodTriangleFloorFrame",grade:"Wood",type:"Frame",buildcost:50,hp:250,decay:3,img:"https://cdn.rusthelp.com/images/256/wood-floor-triangle-frame.webp"},





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
                <img src={Item.img} alt=Item.name>
                <h2>{Item.name}</h2>
            </button>
        {/each}
</section>




<style>
.ScrollableGrid{
    display: grid;
    position: absolute;
    overflow-y: scroll;
    overflow-x: hidden;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
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
    border: #717171 solid 1px;
    border-radius: 10px;
    flex-direction: column;
    width: 80%;
    height: 100%;
    padding: 1%;
    word-wrap: break-word;
    


}
</style>