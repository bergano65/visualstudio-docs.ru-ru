---
title: CA3011. Проверьте код на наличие уязвимостей к внедрению DLL
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
ms.openlocfilehash: a459be8c8ab028581c850f5b5770a95cb70e3510
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237195"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011. Проверьте код на наличие уязвимостей к внедрению DLL

|||
|-|-|
|TypeName|ревиевкодефордллинжектионвулнерабилитиес|
|CheckId|CA3011|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Потенциально ненадежные входные данные HTTP-запроса достигают метода, который загружает сборку.

## <a name="rule-description"></a>Описание правила

При работе с недоверенными входными данными будьте учитывать при загрузке ненадежного кода. Если веб-приложение загружает ненадежный код, злоумышленник может внедрить вредоносные библиотеки DLL в процесс и выполнить вредоносный код.

Это правило пытается найти входные данные из HTTP-запроса, который достигает метода, который загружает сборку.

> [!NOTE]
> Это правило не может отслеживанию данных между сборками. Например, если одна сборка считывает входные данные HTTP-запроса и передает их другой сборке, которая загружает сборку, это правило не выдает предупреждение.

> [!NOTE]
> Существует настраиваемое ограничение на то, насколько глубоким это правило будет анализировать поток данных между вызовами методов. Сведения о настройке ограничения в файле EditorConfig см. в статье [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

Не загружайте ненадежные библиотеки DLL из введенных пользователем данных.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не подавлять предупреждения из этого правила.

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
