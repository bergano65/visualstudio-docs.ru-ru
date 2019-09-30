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
ms.openlocfilehash: 1d001dc306bbb225c4ecc1c0f17bf46619e2d0a7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237264"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008. Проверьте код на наличие уязвимостей к внедрению кода XPath

|||
|-|-|
|TypeName|ревиевкодефоркспасинжектионвулнерабилитиес|
|CheckId|CA3008|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Потенциально недоверенные входные данные HTTP-запроса достигают запроса XPath.

## <a name="rule-description"></a>Описание правила

При работе с недоверенными входными данными будьте учитывать атак путем внедрения XPath. Создание запросов XPath с использованием ненадежных входных данных может позволить злоумышленнику злонамеренно манипулировать запросом для возврата непредвиденного результата и, возможно, раскрывать содержимое запрашиваемого XML.

Это правило пытается найти входные данные из HTTP-запросов, достигнутых выражением XPath.

> [!NOTE]
> Это правило не может отслеживанию данных между сборками. Например, если одна сборка считывает входные данные HTTP-запроса и передает их другой сборке, которая выполняет запрос XPath, это правило не выдает предупреждение.

> [!NOTE]
> Существует настраиваемое ограничение на то, насколько глубоким это правило будет анализировать поток данных между вызовами методов. Сведения о настройке ограничения в файле EditorConfig см. в статье [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

Ниже приведены некоторые подходы к устранению уязвимостей при внедрении XPath.

- Не создавайте запросы XPath на основе вводимых пользователем данных.
- Убедитесь, что входные данные содержат только защищенный набор символов.
- Escape-кавычки.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Если известно, что входные данные проверены как надежные, это предупреждение можно отключить.

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

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
