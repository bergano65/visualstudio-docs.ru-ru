---
title: CA3007. Проверьте код на наличие уязвимостей к открытому перенаправлению
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
ms.openlocfilehash: 0226c0e2e66a6543b81cd8ee674a743766b65f3e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237274"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007. Проверьте код на наличие уязвимостей к открытому перенаправлению

|||
|-|-|
|TypeName|ревиевкодефоропенредиректвулнерабилитиес|
|CheckId|CA3007|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Потенциально недоверенные входные данные HTTP-запроса достигают перенаправления ответа HTTP.

## <a name="rule-description"></a>Описание правила

При работе с недоверенными входными данными будьте учитывать уязвимости открытых перенаправлений. Злоумышленник может воспользоваться уязвимостью с открытым перенаправлением, чтобы использовать веб-сайт для получения правильного URL-адреса, но перенаправить нежелательный посетитель на фишинг или другую вредоносную веб-страницу.

Это правило пытается найти входные данные из HTTP-запросов, которые достигают URL перенаправления HTTP.

> [!NOTE]
> Это правило не может отслеживанию данных между сборками. Например, если одна сборка считывает входные данные HTTP-запроса и передает ее другой сборке, которая отвечает перенаправлению HTTP, это правило не создает предупреждение.

> [!NOTE]
> Существует настраиваемое ограничение на то, насколько глубоким это правило будет анализировать поток данных между вызовами методов. Сведения о настройке ограничения в файле EditorConfig см. в статье [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

Ниже приведены некоторые подходы к исправлению открытых уязвимостей при перенаправлении.

- Не разрешать пользователям инициировать перенаправления.
- Не разрешайте пользователям указывать любую часть URL-адреса в сценарии перенаправления.
- Ограничение перенаправления на предопределенный "список разрешений" для URL-адресов.
- Проверка URL-адресов перенаправления.
- Если это применимо, рассмотрите возможность использования страницы отказа при перенаправлении пользователей с вашего сайта.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Если вы знаете, что входные данные были ограничены предполагаемыми URL-адресами, это предупреждение можно отключить.

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

### <a name="violation"></a>Нарушение

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
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
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
