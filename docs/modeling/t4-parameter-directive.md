---
title: Директива Parameter T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bf92a104d7da419e1d28cc5afe57e96e5020de4f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000891"
---
# <a name="t4-parameter-directive"></a>Директива Parameter T4

В текстовом шаблоне Visual Studio `parameter` директива объявляет свойства в коде шаблона, которые инициализируются из значения, передаваемые из внешнего контекста. Эти значения можно задать при написании кода, который вызывает преобразования текста.

## <a name="using-the-parameter-directive"></a>С помощью параметра-директива

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter` Директива объявляет свойства в коде шаблона, которые инициализируются из значения, передаваемые из внешнего контекста. Эти значения можно задать при написании кода, который вызывает преобразования текста. Значения могут передаваться в `Session` словарь, либо в <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Можно объявить параметры любого типа, поддерживающего удаленное взаимодействие. То есть тип должен быть объявлен с <xref:System.SerializableAttribute>, или он должен быть производным от <xref:System.MarshalByRefObject>. Благодаря этому значения параметра должны быть переданы в домен приложения, в котором обрабатывается шаблон.

 Например можно написать текстовый шаблон со следующим содержимым:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Передача значений параметров в шаблон
 Если вы создаете расширение Visual Studio, например команды меню или обработчик событий, обработка шаблона с помощью службы текстовых шаблонов.

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
 Можно также передать значения как логических данных в <xref:System.Runtime.Remoting.Messaging.CallContext>.

 В следующем примере передается значения с помощью обоих методов:

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Передача значений в текстовый шаблон времени выполнения (предварительно обработанный)
 Обычно необязательно использовать `<#@parameter#>` директиву времени выполнения (предварительно обработанном) текстовых шаблонов. Вместо этого можно определить дополнительный конструктор или задаваемое свойство для сформированного кода, через который передавать значения параметров. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Тем не менее если вы хотите использовать `<#@parameter>` в шаблоне времени выполнения, можно передавать значения к нему, используя словарь сеанса. Например, предположим, вы создали файл как предварительно обработанный шаблон под названием `PreTextTemplate1`. Можно вызвать шаблон в программе, используя следующий код.

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
>  `parameter` Директива не извлекает значения, заданные в `-a` параметр `TextTransform.exe` служебной программы. Чтобы получить эти значения, задайте `hostSpecific="true"` в `template` директивы и используйте `this.Host.ResolveParameterValue("","","argName")`.