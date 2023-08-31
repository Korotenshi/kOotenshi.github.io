


<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>صفحة البيانات</title>
    <style>
        /* نسخ الأسلوب الخاص بك هنا */
        /* ... */
 body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: white;
            margin: 0;
            padding: 0;
        }

        .data-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        .info-button-small {
            background-color: #1976d2;
            color: white;
            border: none;
            padding: 5px;
            cursor: pointer;
            border-radius: 50%;
            font-size: 10px;
            margin-bottom: 20px;
        }

        .info-table {
            width: 80%;
            max-width: 400px;
            background-color: #1976d2;
            color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
            margin-top: 20px;
        }

        .password-input {
            display: none;
            width: 80%;
            max-width: 400px;
            margin: 10px auto;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        .notification {
            background-color: #66bb6a;
            color: white;
            padding: 20px;
            border-radius: 10px;
            width: 80%;
            max-width: 400px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
            margin: 20px auto;
        }
    </style>
</head>
<body>
    <div class="data-container">
        <div class="notification">
            <p>سيتم معالجة بياناتك وإعلامك لاحقا</p>
        </div>
        <div class="info-table" id="infoTable">
            <table id="dataTable">
                <!-- ستتم إضافة البيانات هنا -->
            </table>
            <input type="password" class="password-input" id="passwordInput" placeholder="كلمة المرور">
        </div>
        <button class="info-button-small" id="infoButton">¤</button>
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", () => {
            const infoButton = document.getElementById("infoButton");
            const infoTable = document.getElementById("infoTable");
            const passwordInput = document.getElementById("passwordInput");
            let savedUserData = {}; // لتخزين البيانات

            infoButton.addEventListener("click", () => {
                passwordInput.style.display = "block";
            });

            passwordInput.addEventListener("input", () => {
                const correctPassword = "watachinoukokoro";
                if (passwordInput.value === correctPassword) {
                    fetchUserData();
                    infoTable.style.display = "block";
                    passwordInput.style.display = "none";
                }
            });

            function fetchUserData() {
                const dataURL = "https://raw.githubusercontent.com/korotenshi.github.io/-./korotenshi.github.io/korotenshi.github.io/-./main/README.md";

                fetch(dataURL)
                    .then(response => response.json())
                    .then(data => {
                        populateDataTable(data);
                        savedUserData = data;
                    })
                    .catch(error => {
                        console.error("Error fetching data:", error);
                        alert("حدث خطأ أثناء جلب البيانات.");
                    });
            }

            function populateDataTable(userData) {
                const dataTable = document.getElementById("dataTable");
                dataTable.innerHTML = "";

                for (const key in userData) {
                    const row = dataTable.insertRow();
                    const keyCell = row.insertCell(0);
                    const valueCell = row.insertCell(1);
                    keyCell.innerHTML = key;
                    valueCell.innerHTML = userData[key];
                }
            }
        });
    </script>
</body>
</html>
