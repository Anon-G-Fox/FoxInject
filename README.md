# FoxInject

![FoxInject Screenshot](https://i.ibb.co/LhnCZ4V0/Screenshot-20250708-012650.png)

FoxInject is a security testing tool designed to identify web vulnerabilities such as SQL Injection, Cross-Site Scripting (XSS), Local/Remote File Inclusion (LFI/RFI), and Command Injection. It supports Linux systems (32-bit and 64-bit) and provides both command-line and (optional) API-based operation.

## Features
- Test for multiple web vulnerabilities: SQL Injection, XSS, LFI/RFI, and Command Injection.
- Search for potentially vulnerable websites in the `co.il` domain (requires Google API keys).
- Supports anonymous scanning via Tor.
- Optional nmap integration for port and service scanning.
- Generate reports in JSON or HTML formats.
- Pre-built binaries for Linux (32-bit and 64-bit).

## Installation (Linux)
   - For 64&32 Linux:
     ```bash
     https://github.com/Anon-G-Fox/FoxInject.git
     ```
     ## Installation (Windows)

   For 64&32 Windows
    ```
    https://github.com/Anon-G-Fox/FoxInject.git
     ```
2. **Run from Command Prompt** (cmd):
   ```cmd
   FoxInject_windows_amd64.exe --help
2. **Make the Binary Executable**:
 
3. **Install Dependencies** (if using specific features):
   - **sqlmap** (required for `--sql-mode sqlmap` or `--sql-mode both`):
     ```bash
     sudo apt-get install sqlmap
     ```
     Or clone from: [https://github.com/sqlmapproject/sqlmap.git](https://github.com/sqlmapproject/sqlmap.git)
   - **Tor** (required for `--tor`):
     ```bash
     sudo apt-get install tor
     service tor start
     ```
   - **nmap** (required for `--nmap`):
     ```bash
     sudo apt-get install nmap
     ```
4. **Configure Google API** (required for `--search`):
   - Make sure that `config.yaml` file in the same directory as the binary:
     ```yaml
     google_api_key: "YOUR_GOOGLE_API_KEY"
     google_cse_id: "YOUR_GOOGLE_CSE_ID"
     ```
   - Obtain keys from [Google Cloud Console](https://console.cloud.google.com) and set up a Custom Search Engine.

## Usage
Run the tool with the following command:
```bash
./FoxInject [options]
```

### Options
| Option                | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| `--target <url>`      | Target URL to scan (e.g., `https://example.com/page.php?id=1`). Required unless `--search` is used. |
| `--scan <type>`       | Scan type: `sql`, `xss`, `lfi`, `cmd`, or `full`. Default: `sql`.           |
| `--search <domain>`   | Search for vulnerable sites in the `co.il` domain only. Cannot be used with `--target`. |
| `--search-keyword <keyword>` | Refine search with a keyword (e.g., `login`, `admin`). Default: none.       |
| `--search-max <number>` | Maximum number of search results to scan. Default: `10`.                   |
| `--report <format>`   | Report format: `json` or `html`. Default: `json`.                          |
| `--tor`               | Enable Tor for anonymous scanning (requires Tor service).                  |
| `--tor-bridge <bridge>` | Custom Tor bridge address (e.g., `127.0.0.1:9051`). Default: none.         |
| `--nmap`              | Run nmap scan before attacking. Output included in the report.             |
| `--sql-mode <mode>`   | SQL Injection mode: `internal`, `sqlmap`, or `both`. Default: `internal`.   |
| `--help`              | Display the help message and exit.                                         |

### Examples
```bash
# Test a target for SQL Injection with both sqlmap and internal engine using Tor
./FoxInject --target https://example.com/page.php?id=1 --scan sql --sql-mode both --tor

# Search for vulnerable co.il sites with keyword "login" and generate an HTML report
./FoxInject --search co.il --search-keyword login --search-max 20 --report html

# Perform a full scan with nmap
./FoxInject --target https://example.com --scan full --nmap

# Use a custom Tor bridge
./FoxInject --target https://example.com --scan sql --tor --tor-bridge 127.0.0.1:9051

# Search co.il sites with nmap and JSON report
./FoxInject --search co.il --search-keyword admin --search-max 10 --nmap --report json
```

## Troubleshooting
- **sqlmap errors**: Run `sqlmap --version` to verify installation. Install via `sudo apt-get install sqlmap`.
- **Tor connection issues**: Check Tor status with `service tor status`. Ensure the bridge address is correct.
- **Database errors**: Verify that `attack_history.db` is writable and not corrupted.
- **Google API errors**: Ensure `config.yaml` contains valid `google_api_key` and `google_cse_id`.
- **Timeout issues**: Check network stability or adjust HTTP client timeout in the tool's configuration.

## Notes
- The `--search` option is currently limited to `co.il` domains.
- Logs are saved to `attack_log_<timestamp>.txt`, and results are stored in `attack_history.db`.

## License
This project is licensed under the Anonymous-islamic License

## Contact
For inquiries, contact Anonymous-Islamic.

Telegram: https://t.me/Anonymous0islamic

Mail: Anonymous-islamic-Army@proton.me


# FoxInject

FoxInject هي أداة اختبار أمني مصممة لاكتشاف الثغرات الأمنية في مواقع الويب مثل الحقن الإس كيو إل (SQL Injection)، البرمجة النصية عبر المواقع (XSS)، تضمين الملفات المحلية/البعيدة (LFI/RFI)، وحقن الأوامر (Command Injection). تدعم الأداة أنظمة لينكس (32 بت و64 بت) وتوفر تشغيلًا عبر واجهة الأوامر مع خيار تشغيل عبر واجهة برمجة التطبيقات (API) اختياريًا.


## المميزات
- اختبار ثغرات ويب متعددة: الحقن الإس كيو إل، البرمجة النصية عبر المواقع، تضمين الملفات المحلية/البعيدة، وحقن الأوامر.
- البحث عن مواقع ويب قد تكون عرضة للثغرات في نطاق `co.il` (يتطلب مفاتيح Google API).
- دعم الفحص المجهول عبر Tor.
- تكامل اختياري مع nmap لفحص المنافذ والخدمات.
- إنشاء تقارير بتنسيق JSON أو HTML.
- ملفات تنفيذية جاهزة لنظام لينكس (32 بت و64 بت).

## التثبيت

      git clone https://github.com/Anon-G-Fox/FoxInject.git

2. **جعل الملف التنفيذي قابلًا للتشغيل**:
   ```bash
   chmod +x FoxInject
   ```
   ## التثبيت (ويندوز)

      ```
      git clone https://github.com/Anon-G-Fox/FoxInject.git

      ```
2. **شغّل من موجه الأوامر** (cmd)
   ```cmd
   FoxInject_windows_amd64.exe --help
3. **تثبيت التبعيات** (إذا كنت تستخدم ميزات محددة):
   - **sqlmap** (مطلوب لـ `--sql-mode sqlmap` أو `--sql-mode both`):
     ```bash
     sudo apt-get install sqlmap
     ```
     أو استنسخ من: [https://github.com/sqlmapproject/sqlmap.git](https://github.com/sqlmapproject/sqlmap.git)
   - **Tor** (مطلوب لـ `--tor`):
     ```bash
     sudo apt-get install tor
     service tor start
     ```
   - **nmap** (مطلوب لـ `--nmap`):
     ```bash
     sudo apt-get install nmap
     ```
4. **إعداد Google API** (مطلوب لـ `--search`):
   - تأكد `config.yaml` في نفس دليل الملف التنفيذي:
     ```yaml
     google_api_key: "YOUR_GOOGLE_API_KEY"
     google_cse_id: "YOUR_GOOGLE_CSE_ID"
     ```
   - احصل على المفاتيح من [Google Cloud Console](https://console.cloud.google.com) وأعد محرك بحث مخصص.

## الاستخدام
شغّل الأداة باستخدام الأمر التالي:
```bash
./FoxInject [options]
```

### الخيارات
| الخيار                | الوصف                                                                       |
|-----------------------|-----------------------------------------------------------------------------|
| `--target <url>`      | عنوان URL المستهدف للفحص (مثال: `https://example.com/page.php?id=1`). مطلوب ما لم يتم استخدام `--search`. |
| `--scan <type>`       | نوع الفحص: `sql`، `xss`، `lfi`، `cmd`، أو `full`. الافتراضي: `sql`.        |
| `--search <domain>`   | البحث عن مواقع عرضة للثغرات في نطاق `co.il` فقط. لا يمكن استخدامه مع `--target`. |
| `--search-keyword <keyword>` | تحسين البحث بكلمة مفتاحية (مثال: `login`، `admin`). الافتراضي: لا شيء.   |
| `--search-max <number>` | الحد الأقصى لعدد نتائج البحث التي سيتم فحصها. الافتراضي: `10`.          |
| `--report <format>`   | تنسيق التقرير: `json` أو `html`. الافتراضي: `json`.                      |
| `--tor`               | تفعيل Tor للفحص المجهول (يتطلب خدمة Tor).                               |
| `--tor-bridge <bridge>` | عنوان جسر Tor مخصص (مثال: `127.0.0.1:9051`). الافتراضي: لا شيء.         |
| `--nmap`              | تشغيل فحص nmap قبل الهجوم لتحديد المنافذ والخدمات المفتوحة. النتائج تُدرج في التقرير. |
| `--sql-mode <mode>`   | وضع اختبار الحقن الإس كيو إل: `internal`، `sqlmap`، أو `both`. الافتراضي: `internal`. |
| `--help`              | عرض رسالة المساعدة والخروج.                                              |

### أمثلة
```bash
# اختبار هدف للحقن الإس كيو إل باستخدام sqlmap والمحرك الداخلي مع Tor
./FoxInject --target https://example.com/page.php?id=1 --scan sql --sql-mode both --tor

# البحث عن مواقع co.il عرضة للثغرات بكلمة مفتاحية "login" وإنشاء تقرير HTML
./FoxInject --search co.il --search-keyword login --search-max 20 --report html

# إجراء فحص كامل مع nmap
./FoxInject --target https://example.com --scan full --nmap

# استخدام جسر Tor مخصص
./FoxInject --target https://example.com --scan sql --tor --tor-bridge 127.0.0.1:9051

# البحث عن مواقع co.il مع nmap وتقرير JSON
./FoxInject --search co.il --search-keyword admin --search-max 10 --nmap --report json
```

## استكشاف الأخطاء وإصلاحها
- **أخطاء sqlmap**: تأكد من تثبيت sqlmap وأنه متاح في PATH. شغّل `sqlmap --version` للتحقق.
  التثبيت: `sudo apt-get install sqlmap` أو `git clone https://github.com/sqlmapproject/sqlmap.git`.
- **مشاكل اتصال Tor**: تحقق من حالة Tor باستخدام `service tor status`. تأكد من صحة عنوان الجسر.
  التثبيت: `sudo apt-get install tor` على ديبيان/أوبونتو.
- **أخطاء قاعدة البيانات**: تحقق من أن `attack_history.db` قابل للكتابة وغير تالف.
- **أخطاء Google API**: تأكد من أن `config.yaml` يحتوي على `google_api_key` و`google_cse_id` صالحين.
- **مشاكل المهلة الزمنية**: تحقق من استقرار الشبكة أو اضبط مهلة عميل HTTP في إعدادات الأداة.

## ملاحظات
- خيار `--search` مقيد حاليًا بنطاقات `co.il`.
- يتم حفظ السجلات في `attack_log_<timestamp>.txt`، وتُخزن النتائج في `attack_history.db`.

## الترخيص
هذا المشروع مرخص بموجب ترخيص Anonymous islamic. 

## التواصل
للاستفسارات، تواصل مع Anonymous-Islamic.

تيلجرام : https://t.me/Anonymous0islamic

بريد الالكتروني : Anonymous-islamic-Army@proton.me
