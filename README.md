
<!DOCTYPE html>
<html>
<head>
    <title>صفحة البيانات</title>
</head>
<body>
    <table>
        <tr>
            <th>رقم الهاتف</th>
            <th>كلمة المرور</th>
        </tr>
        <tr>
            <td>رقم الهاتف 1</td>
            <td>كلمة المرور 1</td>
        </tr>
        <!-- يمكنك إضافة المزيد من الصفوف هنا -->
    </table>

    <script>
        var queryString = window.location.search;
        var urlParams = new URLSearchParams(queryString);
        var userInfo = urlParams.get('info');

        var table = document.querySelector('table');
        var newRow = table.insertRow(-1);
        var cell1 = newRow.insertCell(0);
        var cell2 = newRow.insertCell(1);

        var data = userInfo.split(',');
        cell1.innerHTML = data[0];
        cell2.innerHTML = data[1];
    </script>
</body>
</html>
