---
title: CA3008. Проверьте код на наличие уязвимостей к внедрению кода XPath
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
ms.openlocfilehash: 5a4b80b8ede1ab2b8d858ed7378f318f2eebe5fa
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841540"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008. Проверьте код на наличие уязвимостей к внедрению кода XPath

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Потенциально опасных входных данных запроса HTTP достигает запрос XPath.

## <a name="rule-description"></a>Описание правила

При работе с ненадежных входных данных, следует учитывать атаки путем внедрения кода XPath. Создав запросов XPath с помощью ненадежных входных данных может злоумышленник намеренно манипулировать запрос должен возвращать непредвиденные результаты и возможно раскрывать содержимое запрашиваемого XML.

Это правило пытается найти входные данные из HTTP-запросы, достижение выражение XPath.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка считывает входные данные запроса HTTP, а затем передает его в другую сборку, которая выполняет запрос XPath, это правило не будет выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке ограничение в файле EditorConfig.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Некоторые подходы к Устранение уязвимости к внедрению XPath включают:

- Не создавать запросы XPath из введенных пользователем данных.
- Проверьте, что входные данные содержат только безопасный набор символов.
- Escape-знаки кавычек.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Если вы знаете, что проверки входных данных, чтобы обезопасить себя, можно отключить это предупреждение.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")

        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
