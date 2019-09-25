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
ms.openlocfilehash: 42808b3961b18a23f594800f9d0782c908c9b1ba
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237179"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012. Проверьте код на наличие уязвимостей к внедрению регулярных выражений

|||
|-|-|
|TypeName|ревиевкодефоррежексинжектионвулнерабилитиес|
|CheckId|CA3012|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Потенциально недоверенные входные данные запроса HTTP достигают регулярного выражения.

## <a name="rule-description"></a>Описание правила

При работе с ненадежными входными данными будьте учитывать атак путем внедрения регулярных выражений. Злоумышленник может использовать внедрение Regex для злонамеренного изменения регулярного выражения, чтобы сделать регулярное выражение соответствующим, или сделать так, чтобы регулярное выражение использовало чрезмерное количество ПРОЦЕССОРов, что приводит к атаке типа "отказ в обслуживании".

Это правило пытается найти входные данные из HTTP-запросов, достигнутых регулярным выражением.

> [!NOTE]
> Это правило не может отслеживанию данных между сборками. Например, если одна сборка считывает входные данные HTTP-запроса и передает их другой сборке, создающей регулярное выражение, это правило не выдает предупреждение.

> [!NOTE]
> Существует настраиваемое ограничение на то, насколько глубоким это правило будет анализировать поток данных между вызовами методов. Сведения о настройке ограничения в файле EditorConfig см. в статье [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

Ниже перечислены некоторые способы предотвращения внедрения регулярных выражений.

- Всегда используйте [время ожидания совпадений](/dotnet/standard/base-types/best-practices#use-time-out-values) при использовании регулярных выражений.
- Старайтесь не использовать регулярные выражения на основе вводимых пользователем данных.
- Экранирование специальных символов из вводимых пользователем данных <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> путем вызова или другого метода.
- Разрешение только неспециальных символов из вводимых пользователем данных.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Если вы знаете, что вы используете [время ожидания совпадений](/dotnet/standard/base-types/best-practices#use-time-out-values) и что ввод пользователя не имеет специальных символов, это предупреждение можно отключить.

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

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
