---
title: Программирование пользовательского правила извлечения (веб-тест производительности)
description: Сведения о том, как создать собственные правила извлечения на основе класса правила извлечения ExtractionRule.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 09038afd3b8f359ed90639d7f35cb92c04241324
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964606"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Кодирование пользовательского правила извлечения для веб-теста производительности

Можно создавать собственные правила извлечения. Для этого пользовательские правила необходимо наследовать от класса правил извлечения. Правила извлечения являются производными от базового класса <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>.

> [!NOTE]
> Можно также создавать собственные правила проверки. Дополнительные сведения см. в статье [Создание пользовательского кода и подключаемых модулей для нагрузочных тестов](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Создание пользовательского правила извлечения

1. Откройте тестовый проект, содержащий веб-тест производительности.

2. (Необязательно) Создайте отдельный проект библиотеки классов, в котором будет храниться созданное правило извлечения.

    > [!IMPORTANT]
    > Требуемый класс можно создать в том же проекте, в котором находятся тесты. Однако если предполагается повторно использовать правило, то лучше создать для хранения этого правила отдельный проект библиотеки классов. При создании отдельного проекта необходимо выполнить дополнительные действия, описанные в данной процедуре.

3. (Необязательно) В проекте библиотеки классов добавьте ссылку на DDL-библиотеку Microsoft.VisualStudio.QualityTools.WebTestFramework.

4. Создайте класс, производный от класса <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>. Реализуйте члены <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> и <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*>.

5. (Необязательно) Выполните построение нового проекта библиотеки классов.

6. В тестовом проекте добавьте ссылку на проект библиотеки классов, содержащий пользовательское правило извлечения (необязательно).

7. В тестовом проекте откройте веб-тест производительности в **редакторе веб-тестов производительности**.

8. Чтобы добавить пользовательское правило извлечения, щелкните правой кнопкой мыши запрос веб-теста производительности и выберите команду **Добавить правило извлечения**.

     Откроется диалоговое окно **Добавление правила извлечения**. Пользовательское правило проверки появится в списке **Выбрать правило** вместе с предопределенными правилами проверки. Выберите пользовательское правило извлечения и нажмите кнопку **ОК**.

9. Выполните веб-тест производительности.

## <a name="example"></a>Пример

В следующем коде показана реализация пользовательского правила извлечения. Это правило извлекает значение из указанного поля ввода. Данный пример можно использовать в качестве отправной точки для создания собственного правила извлечения.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

Метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> содержит основные функции правила извлечения. Метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> из предыдущего примера принимает аргумент <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs>, который предоставляет ответ, созданный запросом, содержащимся в данном правиле извлечения. Ответ содержит объект <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>, в котором находятся все теги ответа. В объекте <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>отфильтровываются теги "input". Каждый тег input проверяется на наличие атрибута `name`, значение которого равно значению свойства `Name`, предоставленному пользователем. После обнаружения тега с соответствующим атрибутом выполняется попытка извлечь значение, содержащееся в атрибуте `value`, если атрибут value существует. Если он существует, значения атрибутов "name" и "value" данного тега извлекаются и добавляются в контекст веб-теста производительности. Правило извлечения завершается успехом.

## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Кодирование пользовательского правила проверки для веб-теста производительности](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
