# l-
dsad
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <title>نظام تتبع الحاويات</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>نظام تتبع الحاويات</h1>
    <div class="container">
        <input type="text" id="container-number" placeholder="أدخل رقم الحاوية">
        <button id="track-btn">تتبع الحاوية</button>
    </div>
    <div id="result"></div>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    direction: rtl;
    text-align: center;
    background-color: #f2f2f2;
    padding: 50px;
}

h1 {
    color: #333;
}

.container {
    margin: 20px auto;
}

#container-number {
    width: 300px;
    padding: 10px;
    font-size: 16px;
    text-align: right;
}

#track-btn {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    margin-top: 10px;
}

#result {
    margin-top: 30px;
    text-align: right;
    direction: rtl;
}

.result-card {
    background-color: #fff;
    padding: 20px;
    margin-bottom: 20px;
    text-align: right;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.result-card h2 {
    margin-top: 0;
}

.result-card p {
    margin: 5px 0;
}
// بيانات وهمية لتتبع الحاويات
const containers = {
    "ABC1234567": {
        company: "شركة الشحن العالمية",
        status: "في الطريق",
        location: "المحيط الهندي",
        eta: "2023-11-20",
        lastUpdate: "2023-10-30",
        details: "غادرت ميناء سنغافورة متجهة إلى ميناء جدة."
    },
    "XYZ9876543": {
        company: "خطوط المحيط",
        status: "في الميناء",
        location: "ميناء دبي",
        eta: "2023-10-28",
        lastUpdate: "2023-10-28",
        details: "تم الوصول إلى الميناء وتفريغ الحاوية."
    }
    // يمكنك إضافة المزيد من البيانات الوهمية هنا
};

document.getElementById('track-btn').addEventListener('click', function() {
    const containerNumber = document.getElementById('container-number').value.trim();
    const resultDiv = document.getElementById('result');
    resultDiv.innerHTML = '';

    if (containerNumber in containers) {
        const container = containers[containerNumber];
        const card = document.createElement('div');
        card.className = 'result-card';

        const title = document.createElement('h2');
        title.textContent = `تفاصيل الحاوية ${containerNumber}`;
        card.appendChild(title);

        const company = document.createElement('p');
        company.innerHTML = `<strong>الشركة:</strong> ${container.company}`;
        card.appendChild(company);

        const status = document.createElement('p');
        status.innerHTML = `<strong>الحالة:</strong> ${container.status}`;
        card.appendChild(status);

        const location = document.createElement('p');
        location.innerHTML = `<strong>الموقع الحالي:</strong> ${container.location}`;
        card.appendChild(location);

        const eta = document.createElement('p');
        eta.innerHTML = `<strong>وقت الوصول المتوقع:</strong> ${container.eta}`;
        card.appendChild(eta);

        const lastUpdate = document.createElement('p');
        lastUpdate.innerHTML = `<strong>آخر تحديث:</strong> ${container.lastUpdate}`;
        card.appendChild(lastUpdate);

        const details = document.createElement('p');
        details.innerHTML = `<strong>التفاصيل:</strong> ${container.details}`;
        card.appendChild(details);

        resultDiv.appendChild(card);
    } else {
        resultDiv.innerHTML = '<p>لم يتم العثور على الحاوية. يرجى التحقق من رقم الحاوية والمحاولة مرة أخرى.</p>';
    }
});
"DEF1234567": {
    company: "شركة النقل البحري",
    status: "في الطريق",
    location: "البحر الأحمر",
    eta: "2023-11-25",
    lastUpdate: "2023-10-31",
    details: "في طريقها إلى ميناء السويس."
},document.getElementById('track-btn').addEventListener('click', function() {
    const containerNumber = document.getElementById('container-number').value.trim();
    const resultDiv = document.getElementById('result');
    resultDiv.innerHTML = '';

    fetch(`https://api.shippingcompany.com/containers/${containerNumber}`)
        .then(response => response.json())
        .then(data => {
            if (data.found) {
                // عرض البيانات كما في المثال السابق
            } else {
                resultDiv.innerHTML = '<p>لم يتم العثور على الحاوية. يرجى التحقق من رقم الحاوية والمحاولة مرة أخرى.</p>';
            }
        })
        .catch(error => {
            console.error('حدث خطأ:', error);
            resultDiv.innerHTML = '<p>حدث خطأ أثناء جلب البيانات. يرجى المحاولة مرة أخرى لاحقًا.</p>';
        });
});

