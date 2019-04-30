---
title: CA3002. Проверьте код на наличие уязвимостей к межсайтовым сценариям (XSS)
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
ms.openlocfilehash: a10f72297746a1e7bda3c69f8f7daf0efacd20bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541274"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002. Проверьте код на наличие уязвимостей к межсайтовым сценариям (XSS)

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Потенциально опасных входных данных запроса HTTP достигает необработанные выходные данные HTML.

## <a name="rule-description"></a>Описание правила

При работе с ненадежных входных данных из веб-запросов, следует учитывать межузловых сценариев (XSS) атак. Атаки XSS внедряет ненадежных входных данных в необработанные выходных данных HTML, что позволяет ему выполнение вредоносных скриптов или злонамеренно изменить содержимое на веб-странице. Поместив стандартным приемом `<script>` элементы с вредоносным кодом во входных данных. Дополнительные сведения см. в разделе [XSS OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Это правило пытается найти входные данные из HTTP-запросы, достижение необработанные выходные данные HTML.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка считывает входные данные запроса HTTP, а затем передает его в другую сборку, который выводит необработанным HTML, это правило не будет выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке используется ограничение в `.editorconfig` файлов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Вместо использования метода необработанным HTML, используйте метод или свойство этого первого HTML-кодирует его входных данных.
- HTML-кодирование ненадежных данных перед выводом необработанным HTML.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно безопасно подавить предупреждение из этого правила, если:
- Вы знаете, что входные данные проверяются по известных безопасного набора символов, не содержащий HTML-код.
- Вы знаете, что данные HTML-кодировке в виде, не обнаруживаемый этим правилом.

> [!NOTE]
> Это правило может сообщать ложных срабатываний для некоторых методов или свойств, зашифруйте их входных данных.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>Решение

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```