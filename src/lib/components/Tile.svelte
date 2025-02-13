
<script>
    import { dropzone } from "$lib/dnd";
    let {x, y, color, onDrop} = $props()

    // function handleDrop(e) {
    //     e.preventDefault();
    //     console.log(e)
    //     console.log("drop")
    //     e.dataTransfer.dropEffect = 'move';
    //     const data = event.dataTransfer.getData("text/plain");
    //     console.log("data : ",data)
    // }

    // function handleDragOver (e) {
    //     e.preventDefault()
    //     console.log("drag over")
    // }
    
</script>

<div class='tile' 
use:dropzone={{ on_dropzone: (data) => onDrop(data, x, y) }} 
style="background-color :{color} "

>
    <!-- <p>{x};{y}</p> -->
</div>

<style>
    .tile {
        border: 0.02em solid rgb(240, 187, 12);
        border-radius: 2px;
    }

    :global(.droppable){
        outline: 0.1rem solid orange;
    }
    :global(.droppable) * {
        pointer-events: none ;
    }

</style>


