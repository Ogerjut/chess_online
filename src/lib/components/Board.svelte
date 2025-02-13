<script>
    import Tile from "./Tile.svelte";
    import Piece from "./Pieces.svelte";

    const ROWS = 8;
    const COLUMNS = 8;

    // Position initiale des pièces
    let pieces = [
        { type: "rook", color: "black", x: 0, y: 0 },
        { type: "knight", color: "black", x: 1, y: 0 },
        { type: "bishop", color: "black", x: 2, y: 0 },
        { type: "queen", color: "black", x: 3, y: 0 },
        { type: "king", color: "black", x: 4, y: 0 },
        { type: "bishop", color: "black", x: 5, y: 0 },
        { type: "knight", color: "black", x: 6, y: 0 },
        { type: "rook", color: "black", x: 7, y: 0 },

        { type: "pawn", color: "black", x: 0, y: 1 },
        { type: "pawn", color: "black", x: 1, y: 1 },
        { type: "pawn", color: "black", x: 2, y: 1 },
        { type: "pawn", color: "black", x: 3, y: 1 },
        { type: "pawn", color: "black", x: 4, y: 1 },
        { type: "pawn", color: "black", x: 5, y: 1 },
        { type: "pawn", color: "black", x: 6, y: 1 },
        { type: "pawn", color: "black", x: 7, y: 1 },

        { type: "pawn", color: "white", x: 0, y: 6 },
        { type: "pawn", color: "white", x: 1, y: 6 },
        { type: "pawn", color: "white", x: 2, y: 6 },
        { type: "pawn", color: "white", x: 3, y: 6 },
        { type: "pawn", color: "white", x: 4, y: 6 },
        { type: "pawn", color: "white", x: 5, y: 6 },
        { type: "pawn", color: "white", x: 6, y: 6 },
        { type: "pawn", color: "white", x: 7, y: 6 },

        { type: "rook", color: "white", x: 0, y: 7 },
        { type: "knight", color: "white", x: 1, y: 7 },
        { type: "bishop", color: "white", x: 2, y: 7 },
        { type: "queen", color: "white", x: 3, y: 7 },
        { type: "king", color: "white", x: 4, y: 7 },
        { type: "bishop", color: "white", x: 5, y: 7 },
        { type: "knight", color: "white", x: 6, y: 7 },
        { type: "rook", color: "white", x: 7, y: 7 }
    ];

    function handleDrop(data, newX, newY) {
        console.log("DROP : pièce déplacée vers", newX, newY);

        const [oldX, oldY] = data.split(",").map(Number);
        
        pieces = pieces.map(piece => {
            if (piece.x === oldX && piece.y === oldY) {
                return { ...piece, x: newX, y: newY };
            }
            return piece;
        });
    }
</script>

<div class="board">
    {#each Array(ROWS) as _, x }
        {#each Array(COLUMNS) as _, y }
            <Tile x={x} y={y} color={(x + y) % 2 === 0 ? "white" : "#cc4a4a"} onDrop={handleDrop}/>
        {/each}
    {/each}

    <div class="pieces">
        {#each pieces as piece}
            <Piece type={piece.type} color={piece.color} x={piece.x} y={piece.y} />
        {/each}
    </div>
</div>

<style>
    .board {
        margin-left: 128px;
        margin-top: 16px;
        display: grid;
        grid-template-columns: repeat(8, 64px);
        grid-template-rows: repeat(8, 64px);
        position: relative;
        width: 562px;
        height: 562px;
        border: 25px solid rgb(134, 68, 5);
        border-radius: 15px;
    }

    .pieces {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
</style>
