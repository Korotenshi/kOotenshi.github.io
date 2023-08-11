
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
            <td id="phoneNumber"></td>
            <td id="password"></td>
        </tr>
    </table>
    
    <script>
        var queryString = window.location.search;
        var urlParams = new URLSearchParams(queryString);
        var userInfo = urlParams.get('info');

        var data = userInfo.split(', ');
        var phoneNumber = data[0].split(": ")[1];
        var password = data[1].split(": ")[1];
        document.getElementById("phoneNumber").textContent = phoneNumber;
        document.getElementById("password").textContent = password;
    </script>
</body>
</html>
