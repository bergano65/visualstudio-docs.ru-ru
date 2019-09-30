---
title: CA3005. Проверьте код на наличие уязвимостей к внедрению LDAP
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
ms.openlocfilehash: c0c99d5d0adb145a061693f8a83b1f674e05eed4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237338"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005. Проверьте код на наличие уязвимостей к внедрению LDAP

|||
|-|-|
|TypeName|ревиевкодефорлдапинжектионвулнерабилитиес|
|CheckId|CA3005|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Потенциально недоверенные входные данные HTTP-запроса достигают инструкции LDAP.

## <a name="rule-description"></a>Описание правила

При работе с недоверенными входными данными будьте учитывать атак путем внедрения протокола LDAP. Злоумышленник потенциально может выполнять вредоносные инструкции LDAP в информационных каталогах. Приложения, использующие ввод данных пользователем для создания динамических инструкций LDAP для доступа к службам каталогов, особенно уязвимы.

Это правило пытается найти входные данные из HTTP-запросов, достигнутых инструкцией LDAP.

> [!NOTE]
> Это правило не может отслеживанию данных между сборками. Например, если одна сборка считывает входные данные HTTP-запроса и передает ее другой сборке, которая выполняет инструкцию LDAP, это правило не выдает предупреждение.

> [!NOTE]
> Существует настраиваемое ограничение на то, насколько глубоким это правило будет анализировать поток данных между вызовами методов. Сведения о настройке ограничения в файле EditorConfig см. в статье [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Устранение нарушений

Для управляемой пользователем части инструкций LDAP рассмотрите одно из следующих:
- Разрешение только безопасного списка неспециальных символов.
- Запретить Специальный символ
- Экранирование специальных символов.

Дополнительные сведения см. [в статье OWASP по предотвращению внедрения LDAP в Памятка по](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) .

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Если известно, что входные данные проверены или экранированы как защищенные, это предупреждение можно отключить.

## <a name="pseudo-code-examples"></a>Примеры псевдо-кода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*).
        // The resulting LDAP statement will make the server return any object that
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*).
        ' The resulting LDAP statement will make the server return any object that
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
