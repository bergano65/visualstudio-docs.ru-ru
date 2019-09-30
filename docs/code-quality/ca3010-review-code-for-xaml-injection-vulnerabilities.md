---
title: CA3010. Проверьте код на наличие уязвимостей к внедрению кода XAML
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
ms.openlocfilehash: efd30a783f534d76f7f7f3fa18fd181dbe7e98a1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237240"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010. Проверьте код на наличие уязвимостей к внедрению кода XAML

|||
|-|-|
|TypeName|ревиевкодефорксамлинжектионвулнерабилитиес|
|CheckId|CA3010|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Потенциально ненадежные входные данные запроса HTTP достигают <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> метода Load.

## <a name="rule-description"></a>Описание правила

При работе с ненадежными входными данными будьте учитывать атак путем внедрения кода XAML. XAML — это язык разметки, непосредственно представляющий создание и выполнение объекта. Это означает, что элементы, созданные в XAML, могут взаимодействовать с системными ресурсами (например, сетевым доступом и операциями ввода-вывода файловой системы). Если злоумышленник может управлять входными данными для <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> вызова метода Load, злоумышленник может выполнить код.

Это правило пытается найти входные данные из HTTP-запросов <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> , которые достигают метода Load.

> [!NOTE]
> Это правило не может отслеживанию данных между сборками. Например, если одна сборка считывает входные данные HTTP-запроса и передает их другой сборке, которая загружает XAML, это правило не выдает предупреждение.

> [!NOTE]
> Существует настраиваемое ограничение на то, насколько глубоким это правило будет анализировать поток данных между вызовами методов. Сведения о настройке ограничения в файле EditorConfig см. в статье [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

Не загружайте недоверенный код XAML.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не подавлять предупреждения из этого правила.

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
