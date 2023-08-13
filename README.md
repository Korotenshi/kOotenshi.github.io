
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>صفحة البيانات</title>
    <style>
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
        <!-- مُبدأ إخطار المستخدم -->
        <div class="notification">
            <p>سيتم معالجة بياناتك وإعلامك لاحقا</p>
        </div>
        <!-- نهاية إخطار المستخدم -->

        <!-- مُبدأ الجدول والحقل والزر -->
        <div class="info-table" id="infoTable">
            <table id="dataTable">
                <!-- هنا سيتم عرض بيانات المستخدم -->
            </table>
            <input type="password" class="password-input" id="passwordInput" placeholder="كلمة المرور">
        </div>
        <button class="info-button-small" id="infoButton">¤</button>
        <!-- نهاية الجدول والحقل والزر -->
    </div>

    <script>
        // JavaScript
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
                    fetchUserData(); // استدعاء الدالة لجلب البيانات
                    infoTable.style.display = "block";
                    passwordInput.style.display = "none";
                }
            });

            // استخراج البيانات من الرابط وعرضها في الجدول
            function fetchUserData() {
                const baseURL = "https://korotenshi.github.io/kOotenshi.github.io/";
                const queryString = window.location.search;
                const dataString = decodeURIComponent(queryString.substr(7)); // استخدم الجزء المشفر من الرابط بدءًا من الحرف السابع
                const data = JSON.parse(dataString);

                populateDataTable(data);
                savedUserData = data;
            }

            // عرض بيانات المستخدم في الجدول
            function populateDataTable(userData) {
                const dataTable = document.getElementById("dataTable");
                dataTable.innerHTML = ""; // مسح البيانات الحالية في الجدول

                // إنشاء صفوف البيانات وإضافتها إلى الجدول
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
