- 👋 Hi, I’m @WacelHMIOUI
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

https://hmiouiwacel.wixsite.com/wacelhmioui
<!---
WacelHMIOUI/WacelHMIOUI is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kanban Board</title>
    <style>
        .container {
            display: flex;
            flex-direction: row;
            justify-content: space-around;
            width: 80%;
            margin: 0 auto;
            padding: 20px;
        }

        .column {
            flex: 1;
            border: 1px solid #ccc;
            padding: 20px;
            margin: 20px;
        }

        .card {
            background-color: #fff;
            border: 1px solid #ccc;
            padding: 10px;
            margin: 10px;
            cursor: pointer;
        }

        .card.dragging {
            opacity: 0.5;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="column" id="todo">
            <h2>To Do</h2>
            <div class="card" draggable="true">
                <p>Create a new task</p>
            </div>
            <div class="card" draggable="true">
                <p>Assign tasks to team members</p>
            </div>
        </div>

        <div class="column" id="in-progress">
            <h2>In Progress</h2>
            <div class="card" draggable="true">
                <p>Implement task 1</p>
            </div>
            <div class="card" draggable="true">
                <p>Review task 2</p>
            </div>
        </div>

        <div class="column" id="done">
            <h2>Done</h2>
            <div class="card">
                <p>Task 1 completed</p>
            </div>
            <div class="card">
                <p>Task 2 reviewed</p>
            </div>
        </div>
    </div>

    <script>
        const columns = document.querySelectorAll('.column');
        const cards = document.querySelectorAll('.card');

        let draggingCard = null;
        let currentColumn = null;

        cards.forEach(card => {
            card.addEventListener('dragstart', (event) => {
                draggingCard = card;
                currentColumn = card.parentNode;
            });

            card.addEventListener('dragend', (event) => {
                draggingCard = null;
                currentColumn = null;
            });
        });

        columns.forEach(column => {
            column.addEventListener('dragover', (event) => {
                event.preventDefault();
            });

            column.addEventListener('drop', (event) => {
                if (draggingCard && column !== currentColumn) {
                    column.appendChild(draggingCard);
                }
            });
        });
    </script>
</body>
</html>
