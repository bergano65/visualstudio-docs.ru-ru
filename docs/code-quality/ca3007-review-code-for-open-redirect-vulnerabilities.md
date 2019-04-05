---
title: 'CA3007: Просмотр кода для уязвимости открытого перенаправления'
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
ms.openlocfilehash: dbafb6c05a3dba72d1614d6a955e20030a50c6ea
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018584"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Просмотр кода для уязвимости открытого перенаправления

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Потенциально опасных входных данных запроса HTTP достигает ответа перенаправления HTTP.

## <a name="rule-description"></a>Описание правила

При работе с ненадежных входных данных, следует учитывать уязвимости открытого перенаправления. Злоумышленник может воспользоваться уязвимостью открытого перенаправления с помощью веб-сайта расцениваться законным URL-адреса, но перенаправления посетитель ничего не подозревающий фишинга или другие веб-страницу.

Это правило пытается найти входные данные из HTTP-запросы, достижение URL-адрес перенаправления HTTP.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка считывает входные данные запроса HTTP, а затем передает его в другую сборку, которая отвечает на HTTP-перенаправление, это правило не будет выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке используется ограничение в `.editorconfig` файлов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Некоторые подходы к Устранение уязвимости открытого перенаправления включают:

- Запретить пользователям инициировать перенаправления.
- Не позволяет пользователю указать любую часть URL-адрес в сценарии перенаправления.
- Ограничьте перенаправления в стандартных «белый список» URL-адресов.
- Проверить URL-адреса перенаправления.
- Если это применимо, рассмотрите возможность использования Заявление об отказе страницы, когда пользователи перенаправляются на узел.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Если вы знаете, что вы проверите входные данные должны быть ограничены предполагаемого URL-адреса, можно отключить это предупреждение.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

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
