<script>
import { draggable } from "$lib/dnd";

    export let type;
    export let color;
    export let x;
    export let y;

    // Dictionnaire des positions dans la sprite sheet
    const pieceMap = {
        pawn: 5,
        rook: 4,
        knight: 2,
        bishop: 3,
        queen: 1,
        king: 0
    };

    // Coordonnées dans la sprite
    const spriteX = pieceMap[type] * 64;
    const spriteY = color === "black" ? 64 : 0;

    // function handleDragStart(e) {
    //     console.log("début drag")
    //     console.log(e)
    //     e.dataTransfer.setData("text/plain",`${x}, ${y}`)
    // }



    // function handleDragEnd(e) {
    //     console.log('end drag : mouse release or esc')
    // }
</script>

<div class="piece"
    use:draggable={{x , y}}
    style="
    left: {x * 64}px;
    top: {y * 64}px;
    background-position: {-spriteX}px {-spriteY}px;
"
>

</div>

<style>
    .piece {
        width: 64px;
        height: 64px;
        position: absolute;
        background-image: url('pieces_sprite.png');
        background-size: 384px 128px;
    }
</style>
