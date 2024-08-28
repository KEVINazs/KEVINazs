<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pelea con un Árbol</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #87ceeb;
            font-family: sans-serif;
        }
        #gameArea {
            position: relative;
            width: 100vw;
            height: 100vh;
        }
        #character, #tree {
            position: absolute;
            width: 50px;
            height: 50px;
        }
        #character {
            background-color: blue;
            top: 100px;
            left: 100px;
        }
        #tree {
            background-color: green;
            top: 300px;
            left: 300px;
        }
    </style>
</head>
<body>

<div id="gameArea">
    <div id="character"></div>
    <div id="tree"></div>
</div>

<script>
    const character = document.getElementById('character');
    const tree = document.getElementById('tree');

    document.addEventListener('click', (e) => {
        // Mover el personaje a la posición del click
        const x = e.clientX - character.offsetWidth / 2;
        const y = e.clientY - character.offsetHeight / 2;

        character.style.left = `${x}px`;
        character.style.top = `${y}px`;

        // Chequear si el personaje está cerca del árbol
        if (isColliding(character, tree)) {
            alert('¡Estás peleando con el árbol!');
        }
    });

    function isColliding(div1, div2) {
        const rect1 = div1.getBoundingClientRect();
        const rect2 = div2.getBoundingClientRect();

        return !(
            rect1.right < rect2.left || 
            rect1.left > rect2.right || 
            rect1.bottom < rect2.top || 
            rect1.top > rect2.bottom
        );
    }
</script>

</body>
</html>
