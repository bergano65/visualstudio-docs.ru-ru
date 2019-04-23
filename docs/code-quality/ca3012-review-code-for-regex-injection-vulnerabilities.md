---
title: CA3012. Проверьте код на наличие уязвимостей к внедрению регулярных выражений
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
ms.openlocfilehash: 114b44ec566554c81f5caf3b8ac474f9c5a75c07
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106258"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012. Проверьте код на наличие уязвимостей к внедрению регулярных выражений

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Потенциально опасных входных данных запроса HTTP достигает регулярное выражение.

## <a name="rule-description"></a>Описание правила

При работе с ненадежных входных данных, следует учитывать атаки путем внедрения кода регулярное выражение. Злоумышленник может использовать регулярное выражение внедрения злонамеренно изменить регулярное выражение, чтобы сделать регулярное выражение соответствует нежелательный результат, или для регулярных выражений, которые потребляют слишком много ресурсов ЦП, приводит к отказу в обслуживании.

Это правило пытается найти входные данные из HTTP-запросы, достижение регулярное выражение.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка считывает входные данные запроса HTTP, а затем передает его в другую сборку, которая создает регулярное выражение, это правило не будет выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке используется ограничение в `.editorconfig` файлов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Включить некоторые методы устранения рисков от межсайтовых регулярное выражение:

- Всегда используйте [соответствует времени ожидания](/dotnet/standard/base-types/best-practices#use-time-out-values) при использовании регулярных выражений.
- Старайтесь не использовать регулярные выражения, на основе ввода пользователя.
- Пропуск специальных знаков из введенных пользователем данных, вызвав <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> или другого метода.
- Разрешить только специальные символы из введенных пользователем данных.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Если вы знаете, что вы используете [соответствует времени ожидания](/dotnet/standard/base-types/best-practices#use-time-out-values) и входные данные пользователя предоставляется бесплатно специальных символов, необходимо отключить это предупреждение.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
