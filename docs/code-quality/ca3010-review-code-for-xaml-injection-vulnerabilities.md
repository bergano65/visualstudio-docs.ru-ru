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
ms.openlocfilehash: 965e0d800bd7c725236d96499d2bf2d441b40412
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841092"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010. Проверьте код на наличие уязвимостей к внедрению кода XAML

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

HTTP-запрос, потенциально небезопасных входных данных достигает <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> метод Load.

## <a name="rule-description"></a>Описание правила

При работе с ненадежных входных данных, следует учитывать атаки путем внедрения кода XAML. XAML — это язык разметки, непосредственно представляющий создание и выполнение объекта. Это означает, что элементы, созданные в XAML можно взаимодействовать с системными ресурсами (например, сетевой доступ и файловой системы ввода-ВЫВОДА). Если злоумышленник может управлять входными данными для <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> загрузить вызова метода, а затем злоумышленник может исполнить код.

Это правило пытается найти входные данные из HTTP-запросов, который достигает <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> метод Load.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка считывает входные данные запроса HTTP, а затем передает его в другую сборку, которая загружает XAML, это правило не будет выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке ограничение в файле EditorConfig.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Не загружать недоверенных XAML.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не отключить предупреждения из этого правила.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

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
