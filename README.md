<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نموذج طلب دعم</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #e9ecef;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            direction: rtl;
        }

        .container {
            max-width: 100%;
            width: 100%;
            padding: 15px;
            background: #fff;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
            border: 1px solid #ddd;
            text-align: right;
        }

        .logo {
            display: block;
            margin: 0 auto 20px;
            width: 80%;
            max-width: 100px;
        }

        h1 {
            color: #004085;
            margin-bottom: 20px;
            font-size: 20px;
            text-align: center;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #333;
        }

        input, select, textarea, button {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 5px;
            margin-bottom: 15px;
            font-size: 14px;
            box-sizing: border-box;
            transition: border-color 0.3s ease;
            text-align: right;
        }

        input:focus, select:focus, textarea:focus {
            border-color: #007bff;
            outline: none;
        }

        button {
            background-color: #004085;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
            padding: 12px;
        }

        button:hover {
            background-color: #003366;
        }

        #statusMessage {
            text-align: center;
            margin-top: 15px;
            font-size: 16px;
            color: #28a745;
            display: none;
        }

        @media (max-width: 600px) {
            .container {
                padding: 10px;
                max-width: 100%;
            }

            h1 {
                font-size: 18px;
            }

            .logo {
                width: 60%;
            }

            input, select, textarea, button {
                font-size: 16px;
            }

            button {
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="https://assets.onecompiler.app/42r523uca/42vf4yhs4/JO.png" alt="شعار" class="logo">
        <button onclick="toggleLanguage()">تغيير اللغة</button>
        <h1 id="formTitle">نموذج طلب دعم</h1>
        <form id="supportForm">
            <label for="organization" id="organizationLabel">اسم الجهة الحكومية:</label>
            <select id="organization" name="organization" required>
                <option value="وزارة الطاقة والثروة المعدنية" data-whatsapp="+962775573157" data-email="">وزارة الطاقة والثروة المعدنية</option>
                <option value="هيئة تنظيم قطاع الطاقة والمعادن" data-whatsapp="" data-email="info@emrc.gov.jo">هيئة تنظيم قطاع الطاقة والمعادن (EMRC)</option>
                <option value="شركة الكهرباء الوطنية" data-whatsapp="" data-email="info@nepco.com.jo">شركة الكهرباء الوطنية (NEPCO)</option>
                <option value="صندوق تشجيع الطاقة المتجددة وترشيد الطاقة" data-whatsapp="" data-email="info@jreeef.gov.jo">صندوق تشجيع الطاقة المتجددة وترشيد الطاقة (JREEEF)</option>
            </select>
            
            <label for="name" id="nameLabel">اسمك الكامل:</label>
            <input type="text" id="name" name="name" required>
            
            <label for="nationalID" id="nationalIDLabel">الرقم الوطني:</label>
            <input type="text" id="nationalID" name="nationalID" required>
            
            <label for="phone" id="phoneLabel">رقم الهاتف:</label>
            <input type="tel" id="phone" name="phone" required>
            
            <label for="email" id="emailLabel">البريد الإلكتروني:</label>
            <input type="email" id="email" name="email" required>
            
            <label for="issue" id="issueLabel">المشكلة التي تحتاج الدعم من أجلها:</label>
            <textarea id="issue" name="issue" rows="4" required></textarea>
            
            <button type="button" onclick="openWhatsAppOrEmail()" id="submitBtn">إرسال</button>
        </form>
        <div id="statusMessage">تم إرسال الطلب بنجاح!</div>
    </div>

    <script>
        let isArabic = true;

        function toggleLanguage() {
            isArabic = !isArabic;

            if (isArabic) {
                document.documentElement.lang = 'ar';
                document.body.dir = 'rtl';
                document.getElementById('formTitle').textContent = 'نموذج طلب دعم';
                document.getElementById('organizationLabel').textContent = 'اسم الجهة الحكومية:';
                document.getElementById('nameLabel').textContent = 'اسمك الكامل:';
                document.getElementById('nationalIDLabel').textContent = 'الرقم الوطني:';
                document.getElementById('phoneLabel').textContent = 'رقم الهاتف:';
                document.getElementById('emailLabel').textContent = 'البريد الإلكتروني:';
                document.getElementById('issueLabel').textContent = 'المشكلة التي تحتاج الدعم من أجلها:';
                document.getElementById('submitBtn').textContent = 'إرسال';
            } else {
                document.documentElement.lang = 'en';
                document.body.dir = 'ltr';
                document.getElementById('formTitle').textContent = 'Support Request Form';
                document.getElementById('organizationLabel').textContent = 'Government Organization Name:';
                document.getElementById('nameLabel').textContent = 'Full Name:';
                document.getElementById('nationalIDLabel').textContent = 'National ID:';
                document.getElementById('phoneLabel').textContent = 'Phone Number:';
                document.getElementById('emailLabel').textContent = 'Email Address:';
                document.getElementById('issueLabel').textContent = 'Issue for which you need support:';
                document.getElementById('submitBtn').textContent = 'Submit';
            }
        }

        function openWhatsAppOrEmail() {
            const name = document.getElementById('name').value;
            const nationalID = document.getElementById('nationalID').value;
            const phone = document.getElementById('phone').value;
            const email = document.getElementById('email').value;
            const issue = document.getElementById('issue').value;
            const organizationElement = document.getElementById('organization');
            const organization = organizationElement.value;
            const whatsappNumber = "+962781339210";
            const emailRecipient = organizationElement.options[organizationElement.selectedIndex].dataset.email;

            if (!name || !nationalID || !phone || !email || !issue) {
                alert("يرجى ملء جميع الحقول.");
                return;
            }

            const message = `
                السادة/ ${organization} المحترمين،

                تحية طيبة وبعد،

                أود أن أرفع إلى مقامكم طلب الدعم حول الموضوع التالي:

                المشكلة: ${issue}.

                أود من حضرتكم النظر في طلبي والتكرم باتخاذ اللازم لإيجاد حل لهذه المشكلة.

                بياناتي هي كالتالي:
                - الاسم الكامل: ${name}
                - الرقم الوطني: ${nationalID}
                - رقم الهاتف: ${phone}
                - البريد الإلكتروني: ${email}

                أرجو منكم التواصل معي في أقرب وقت ممكن لمتابعة هذا الطلب.

                وتفضلوا بقبول فائق الاحترام والتقدير.

                ${name}
            `;

            const whatsappURL = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;
            const emailURL = `mailto:${emailRecipient}?subject=طلب دعم&body=${encodeURIComponent(message)}`;

            window.open(whatsappURL, '_blank');
            window.open(emailURL, '_blank');
            document.getElementById('statusMessage').style.display = 'block';
        }
    </script>
</body>
</html>
