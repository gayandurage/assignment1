<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    
    <title>Assignment 03</title>
    <style>
       
        #drawingCanvas {
            border: 1px solid #e90909;
        }

        .buttons {
            position: fixed;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
        }
        
        #tesxtareablock,
        #drawingareablock {
            display: none;
            margin-top: 10px;
        }

        
        #surveyformblock {
            display: none;
            margin-top: 10px;
            margin-right: 60%;
            border: 2px solid green;
            padding: 10px;
        }

        .buttons button {
            margin-right: 10px;
        }
    </style>
</head>
<body>

<h1>Assignment 03</h1>


<div class="buttons">
    <button id="stextarea", style="color:#e90909">Click Me to Get Text Area</button>
    <button id="sdrawingbutton", style="color:blue">Click Me to Get Drawing Area</button>
    <button id="ssurveydetails", style="color: green;">Click Me to Get Survey Form</button>
</div>


<div id="tesxtareablock">
    <label for="textarea", margin="10" , style="color: blue;">Text Area:</label>
    <br>
    <textarea id="textarea" rows="2" cols="25"></textarea>
</div>


<div id="drawingareablock">
    <label for="drawingCanvas", margin="10", style="color: red;">Drawing Area:</label>
    <br>
    <canvas id="drawingCanvas" width="200" height="100"></canvas>
</div>


<div id="surveyformblock">
    <label margin="10" , style="color: green;">Survey Form:</label>
    <br>
    <br>
    <form>
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="id">ID:</label>
        <input type="text" id="id" name="id" required><br><br>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br>

        <div class="brands">
            <label class="brandcheckbox">
                <input type="checkbox" name="Cbrands" value="sony"> Sony
            </label>
            <label class="brandcheckbox">
                <input type="checkbox" name="Cbrands" value="hp"> HP
            </label>
            <label class="brandcheckbox">
                <input type="checkbox" name="Cbrands" value="dell"> Dell
            </label>
        </div>

        <div class="accessories">
            <label class="accessoriesblock">
                <input type="checkbox" name="accessory" value="headset"> Headset
            </label>
            <label class="accessoriesblock">
                <input type="checkbox" name="accessory" value="webcam"> Webcam
            </label>
            <label class="accessoriesblock">
                <input type="checkbox" name="accessory" value="mouse"> Mouse
            </label>
            <label class="accessoriesblock">
                <input type="checkbox" name="accessory" value="printer"> Printer
            </label>
        </div>

        <label for="favourite">Favorite IDE:</label>
        <select id="favourite" name="favourite">
            <option value="eclipse">Eclipse</option>
            <option value="vscode">VSCode</option>
            <option value="intellij">IntelliJ</option>
        </select><br>

        <input type="submit" value="Submit">
    </form>
</div>

<script>
   
    document.getElementById('stextarea').addEventListener('click', function() {
        toggleVisibility('tesxtareablock');
    });

   
    document.getElementById('sdrawingbutton').addEventListener('click', function() {
        toggleVisibility('drawingareablock');
        initializeDrawing();
    });

    
    document.getElementById('ssurveydetails').addEventListener('click', function() {
        toggleVisibility('surveyformblock');
    });

   
    function toggleVisibility(elementId) {
        var element = document.getElementById(elementId);
        element.style.display = (element.style.display === 'none' || element.style.display === '') ? 'block' : 'none';
    }

    function initializeDrawing() {
        var canvas = document.getElementById('drawingCanvas');
        context = canvas.getContext('2d');

        canvas.addEventListener('mousedown', startDrawing);
        canvas.addEventListener('mousemove', draw);
        canvas.addEventListener('mouseup', stopDrawing);
        canvas.addEventListener('mouseout', stopDrawing);
    }

  
    function startDrawing(e) {
        isDrawing = true;
        draw(e);
    }

   
    function draw(e) {
        if (!isDrawing) return;

        context.lineWidth = 5;
        context.lineCap = 'round';
        context.strokeStyle = '#000';

        context.lineTo(e.clientX - e.target.offsetLeft, e.clientY - e.target.offsetTop);
        context.stroke();
        context.beginPath();
        context.moveTo(e.clientX - e.target.offsetLeft, e.clientY - e.target.offsetTop);
    }

    
    function stopDrawing() {
        isDrawing = false;
        context.beginPath();
    }


</script>

</body>
</html>
