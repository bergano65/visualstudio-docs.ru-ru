---
title: CA3004. Проверьте код на наличие уязвимостей к раскрытию информации
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
ms.openlocfilehash: 82f763d9a6b1ec27975aa80054456a6bbbaeaa2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541273"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004. Проверьте код на наличие уязвимостей к раскрытию информации

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Сообщение исключения, трассировки стека или строковое представление достигает выходные веб-данные.

## <a name="rule-description"></a>Описание правила

Раскрытие сведений об исключении дает представление о внутренних компонентов приложения, что злоумышленники могут получить найти другие уязвимости, чтобы воспользоваться злоумышленники.

Это правило пытается найти сообщение об исключении, трассировку стека или строковое представление, выводимые в HTTP-ответ.

> [!NOTE]
> Это правило не может отслеживать данные между сборками. Например если одна сборка перехватывает исключение и затем передает его в другую сборку, которая выдает исключение, это правило не будет выдавать предупреждение.

> [!NOTE]
> Нет настраиваемое ограничение на глубину это правило будет анализировать поток данных между вызовами метода. См. в разделе [Analyzer Configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) по настройке используется ограничение в `.editorconfig` файлов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Не выводить сведения об исключении для HTTP-ответов. Вместо этого предоставьте сообщение об общей ошибке. См. в разделе [OWASP обработка ошибок страницы](https://www.owasp.org/index.php/Error_Handling) Дополнительные рекомендации.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Если вы знаете, что выходные данные web находится в пределах границы доверия приложения и никогда не предоставляется вне, его можно отключить это предупреждение. Это случается редко. Имейте в виду, что со временем может меняться границы доверия приложения и потоки данных.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>Решение

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```