<html>
<head>
</head>
<body>
    <div id = "score">0</div>
    <canvas id="board" width = "720" height = "420"></canvas>
    <style> 
        #score{ 
            text-align: center;
            font-size: 90px; 
        }
        #board{ 
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            border-color: blue;
            border-style: solid;
        }
    </style>
</body> 
<script>
    const board = document.getElementById("board");
    const board_ctx = board.getContext("2d");
    let score = 0; //counter
    let newdirection = false;
    let food_x; 
    let food_y;
    let dx = 10;//speed at which the snake parts travel
    let dy = 0;
    
    
  let snake = [
      {x: 360, y: 210},
      {x: 350, y: 210},
      {x: 340, y: 210},
      {x: 330, y: 210},
      {x: 320, y: 210}
    ]

    //Actual commands
    main(); 
    makeFood;
    document.addEventListener("keydown", newdirection);

    function main(){ 
        if (end_game()){ 
            return; 
        }
        newdirection = false; 
        setTimeout(function onTick() {
            make_board(); 
            makeFood(); 
            move(); 
            updateSnake(); 
            update(); 
        }, 100)
    }

    function make_board() {
      board_ctx.fillStyle = board_background;
      board_ctx.strokestyle = board_border;
      board_ctx.fillRect(0, 0, board.width, board.height);
      board_ctx.strokeRect(0, 0, board.width, board.height);
    }

    function updateSnake(){ 
        snake.forEach(newPart)
    }

    function newPart(snakePart){ 
        board_ctx.fillStyle = "green"; 
        board_ctx.strokestyle = "black"; 
        board_ctx.fillStyle(snakePart.x, snakePart.y, 20, 20); 
        board_ctx.strokeRect(snakePart.x, snakePart.y, 20, 20); 
    }

    function makeFood(){ 
        board_ctx.fillStyle = 'red';
        board_ctx.strokestyle = 'black';
        board_ctx.fillRect(food_x, food_y, 20, 20);
        board_ctx.strokeRect(food_x, food_y, 20, 20);
    }

    function new_food(){ 
        food_x = randomizer(0, board.width - 10); 
        food_y = randomizer(0, board.height - 10); 
        snake.forEach(function eaten(part) {
            const ate = part.x == food_x && part.y == food_y;
            if (ate)
            new_food();
        });
        }

    function randomizer(min, max){ 
        difference = max - min; 
        return Math.round(Math.random() * (difference) + min / 10) * 10; 
    }

    function direction(event){ 
        const LEFT_KEY = 37;
        const RIGHT_KEY = 39;
        const UP_KEY = 38;
        const DOWN_KEY = 40;
        if (newdirection) 
            return;
        newdirection = true;
        const keyPressed = event.keyCode;
        const goingUp = dy === -10;
        const goingDown = dy === 10;
        const goingRight = dx === 10;
        const goingLeft = dx === -10;
        if (keyPressed === LEFT_KEY && !goingRight) {
            dx = -10;
            dy = 0;
        }
        if (keyPressed === UP_KEY && !goingDown) {
            dx = 0;
            dy = -10;
        }
        if (keyPressed === RIGHT_KEY && !goingLeft) {
            dx = 10;
            dy = 0;
        }
        if (keyPressed === DOWN_KEY && !goingUp) {
            dx = 0;
            dy = 10;
        }
    }

    function move(){ 
        const head = {x: snake[0].x + dx, y: snake[0].y + dy}; 
        snake.unshift(head); 
        const eat = snake[0].x == food_x && snake[0].y == food_y; 
        if (eat){ 
            score += 1;
            document.getElementById('score').innerHTML = score; 
            new_food();  
        }
        else{ 
            snake.pop(); 
        }
    }

    function end_game(){ 
        for (let i = 0; i<snake.length; i++){ 
            if (snake[i].x == snake[0].x && snake[i].y == snake[0].y)
                return true;
        }
        const leftWall = snake[0].x < 0;
        const rightWall = snake[0].x > border.width - 10; 
        const upperWall = snake[0].y < 0; 
        const lowerWall = snake[0].y > border.height - 10; 
        return leftWall || rightWall || upperWall || lowerWall; 
    }
</script>
</html>
