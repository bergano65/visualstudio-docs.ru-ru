---
title: CA3003. Проверьте код на наличие уязвимостей к внедрению пути к файлу
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9e43dcdf1e923cb7bc4a98b17fd0be71b7927eb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237397"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003. Проверьте код на наличие уязвимостей к внедрению пути к файлу

|||
|-|-|
|TypeName|ревиевкодефорфилепасинжектионвулнерабилитиес|
|CheckId|CA3003|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Потенциально недоверенные входные данные запроса HTTP достигают пути к операции с файлом.

## <a name="rule-description"></a>Описание правила

При работе с ненадежными входными данными из веб-запросов будьте учитывать, используя управляемые пользователем входные данные при указании путей к файлам. Злоумышленник может прочитать непреднамеренно созданный файл, что приводит к раскрытию информации конфиденциальных данных. Или злоумышленник может выполнить запись в непреднамеренном файле, что приведет к несанкционированному изменению конфиденциальных данных или нарушению безопасности сервера. Распространенным методом атаки является [обход пути](https://www.owasp.org/index.php/Path_Traversal) для доступа к файлам за пределами требуемого каталога.

Это правило пытается найти входные данные из HTTP-запросов, которые достигнут путь в операции с файлом.

> [!NOTE]
> Это правило не может отслеживанию данных между сборками. Например, если одна сборка считывает входные данные HTTP-запроса и передает их в другую сборку, которая выполняет запись в файл, это правило не выдает предупреждение.

> [!NOTE]
> Существует настраиваемое ограничение на то, насколько глубоким это правило будет анализировать поток данных между вызовами методов. Сведения о настройке ограничения в файле EditorConfig см. в статье [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

- По возможности ограничьте пути к файлам на основе вводимых пользователем данных в явно известном надежном списке.  Например, если приложению требуется доступ к «Red. txt», «Green. txt» или «Blue. txt», разрешите только эти значения.
- Проверьте наличие ненадежных имен файлов и убедитесь, что оно имеет правильный формат.
- При указании путей используйте полные имена путей.
- Избегайте потенциально опасных конструкций, таких как переменные среды PATH.
- Допускайте только длинные имена файлов и проверку длинных имен, если пользователь отправляет короткие названия.
- Ограничьте ввод конечных пользователей допустимыми символами.
- Отклоните имена с превышением длины MAX_PATH.
- Обрабатывайте имена файлов буквально без интерпретации.
- Определите, представляет ли имя файла файл или устройство.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Если вы проверили входные данные, как описано в предыдущем разделе, это предупреждение можно отключить.

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is:
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display
            // The content to the webpage.
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is:
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display
            ' The content to the webpage.
        End Using
    End Sub
End Class
```
