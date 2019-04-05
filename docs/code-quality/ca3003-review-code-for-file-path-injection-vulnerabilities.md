---
title: 'CA3003: Просмотр кода для уязвимости к внедрению путь файла'
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
ms.openlocfilehash: c20d3efb9ea84a7e8bb22288303313ef44b2b795
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018595"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: Просмотр кода для уязвимости к внедрению путь файла

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Потенциально опасных входных данных запроса HTTP достигает путь файла операции.

## <a name="rule-description"></a>Описание правила

При работе с ненадежных входных данных из веб-запросов, следует учитывать при указании пути к файлам, с помощью управляемой пользователем входных данных. Злоумышленник может иметь возможность читать файл непредвиденные приводит раскрытие конфиденциальных данных. Или, злоумышленник может быть возможность записи в файл непредвиденным, приводит к несанкционированных изменений конфиденциальных данных или нарушения безопасности сервера. — Это распространенный способ злоумышленник [пути обхода](https://www.owasp.org/index.php/Path_Traversal) для доступа к файлам за пределами предполагаемого каталога.

Это правило пытается найти входные данные из HTTP-запросы, достижение путь в операции с файлом.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка считывает входные данные запроса HTTP, а затем передает его в другую сборку, которая записывает в файл, это правило не будет выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке используется ограничение в `.editorconfig` файлов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Если это возможно ограничьте пути к файлам на основе ввода пользователя в список явно известных надежных.  Например если приложению требуется только для доступа к «red.txt», «green.txt» или «blue.txt», разрешите только эти значения.
- Проверьте наличие недоверенных имена файлов и проверить, что имя правильно сформированы.
- Используйте полные пути, при указании пути.
- Избегайте потенциально опасных конструкций, таких как переменные среды path.
- Принимают длинные имена файлов и проверить длинное имя, если пользователь отправляет короткие имена.
- Ограничьте ввод конечного пользователя допустимые символы.
- Отклоните имена, где MAX_PATH превышена.
- Обработка имен файлов буквально, без интерпретации.
- Определите, представляет ли имя файла в файл или устройство.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Если вы проверили входных данных, как описано в предыдущем разделе, можно отключить это предупреждение.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

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
