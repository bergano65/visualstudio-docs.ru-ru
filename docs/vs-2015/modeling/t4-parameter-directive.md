---
title: T4 Директива Parameter | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c7971dc3402a344a5318fd8415404e7a45ae8485
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994418"
---
# <a name="t4-parameter-directive"></a>Директива Parameter T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] текстового шаблона `parameter` директива объявляет свойства в коде шаблона, которые инициализируются из значения, передаваемые из внешнего контекста. Эти значения можно задать при написании кода, который вызывает преобразования текста.  
  
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
 Если вы создаете [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширение, например команды меню или обработчик событий, можно обработать шаблон с помощью службы текстовых шаблонов:  
  
```csharp  
// Get a service provider – how you do this depends on the context:  
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
>  `parameter` Директива не извлекает значения, заданные в `–a` параметр `TextTransform.exe` служебной программы. Чтобы получить эти значения, задайте `hostSpecific="true"` в `template` директивы и используйте `this.Host.ResolveParameterValue("","","argName")`.
