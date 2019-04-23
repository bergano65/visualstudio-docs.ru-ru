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
ms.openlocfilehash: a6f3a2db89e35408a19cec47c971821fedf5f85a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089547"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011. Проверьте код на наличие уязвимостей к внедрению DLL

|||
|-|-|
|TypeName|ReviewCodeForDllInjectionVulnerabilities|
|CheckId|CA3011|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Потенциально небезопасных HTTP-запроса, что входные данные достигает метод загружает сборку.

## <a name="rule-description"></a>Описание правила

При работе с ненадежных входных данных, следует учитывать загрузки ненадежного кода. Если веб-приложение загружает ненадежный код, злоумышленнику можно внедрить вредоносный DLL-библиотеки в процесс, а также выполнения вредоносного кода.

Это правило пытается найти входные данные из HTTP-запроса, подходящее для метода, который загружает сборки.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка считывает входные данные запроса HTTP, а затем передает его в другую сборку, которая загружает сборку, это правило не выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке используется ограничение в `.editorconfig` файлов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Не загружать недоверенных библиотек DLL из введенных пользователем данных.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не отключить предупреждения из этого правила.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

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
