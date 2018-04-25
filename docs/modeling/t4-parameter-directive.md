---
title: Директива Parameter T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a44204fa12c3ef549ce31f2e02f9f79247a4580f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="t4-parameter-directive"></a>Директива Parameter T4

В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] текстового шаблона `parameter` директива объявляет свойства в коде шаблона, которые инициализируются из значений, поступающих из внешнего контекста. Эти значения можно задать при написании кода, который вызывает преобразование текста.

## <a name="using-the-parameter-directive"></a>С помощью параметра-директива

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter` Директива объявляет свойства в коде шаблона, которые инициализируются из значений, поступающих из внешнего контекста. Эти значения можно задать при написании кода, который вызывает преобразование текста. Значения могут передаваться либо в `Session` словаря, либо в <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Можно объявить параметры любого типа может быть удаленным. То есть, тип должен объявляться с <xref:System.SerializableAttribute>, или он должен быть производным от <xref:System.MarshalByRefObject>. Это позволяет значения параметра должны быть переданы в домен приложения, в котором обрабатывается шаблон.

 Например вы напишете текстовый шаблон со следующим содержимым:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>Передача значений параметров шаблона
 При создании [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения, такими как команды меню или обработчик событий, можно обработать шаблон, с помощью службы текстовых шаблонов:

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));

```

## <a name="passing-values-in-the-call-context"></a>Передача значений в контексте вызова
 Можно также передавать значения виде логических данных в <xref:System.Runtime.Remoting.Messaging.CallContext>.

 В следующем примере значения передаются с помощью обоих методов:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test

```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Передача значений в текстовом шаблоне времени выполнения (предварительно обработанный)
 Обычно необязательно использовать `<#@parameter#>` директивы времени выполнения (предварительно обработанном) текстовых шаблонов. Вместо этого можно определить дополнительный конструктор или задаваемое свойство для сформированного кода, через который передачи значений параметров. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Тем не менее если вы хотите использовать `<#@parameter>` в шаблон времени выполнения, можно передавать значения к нему с помощью словаря сеанса. Например, предположим, созданный файл как предварительно обработанный шаблон называется `PreTextTemplate1`. Можно вызвать шаблон в программе, используя следующий код.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Получение аргументов из TextTemplate.exe

> [!IMPORTANT]
>  `parameter` Директива не извлекает значения, заданные в `-a` параметр `TextTransform.exe` программы. Чтобы получить эти значения, задайте `hostSpecific="true"` в `template` директивы и используйте `this.Host.ResolveParameterValue("","","argName")`.