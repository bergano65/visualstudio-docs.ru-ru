---
title: "T4 Parameter Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Parameter Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В текстовом шаблоне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] директива `parameter` объявляет свойства кода шаблона, инициализируемые из значений, которые поступают из внешнего контекста.  Можно задать эти значения при написании кода, вызывающего преобразование текста.  
  
## Использование директивы Parameter  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 Директива `parameter` объявляет свойства в коде шаблона, которые инициализируются из значений, поступающих из внешнего контекста.  Можно задать эти значения при написании кода, вызывающего преобразование текста.  Значения могут передаваться либо в словарь `Session`, либо в тип <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Можно объявлять параметры любого типа с поддержкой удаленного взаимодействия.  Это значит, что тип должен объявляться с типом <xref:System.SerializableAttribute> или наследоваться от типа <xref:System.MarshalByRefObject>.  Это позволяет передавать значения параметров в домен приложения, в котором обрабатывается шаблон.  
  
 Например, можно создать текстовый шаблон со следующим содержимым:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## Передача значений параметров в шаблон  
 При создании расширения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], такого как команда меню или обработчик событий, можно обработать шаблон с использованием служб текстовых шаблонов:  
  
```c#  
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
  
## Передача значений в контексте вызова  
 Кроме того, можно передавать значения в виде логических данных в типе <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 В следующем примере значения передаются с использованием обоих методов:  
  
```c#  
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
  
## Передача значений в текстовый шаблон времени выполнения \(предварительно обработанный\)  
 Как правило, нет необходимости использовать директиву `<#@parameter#>` с текстовыми шаблонами времени выполнения \(предварительно обработанными\).  Вместо этого можно определить дополнительный конструктор или задаваемое свойство для сформированного кода, с помощью которого будут передаваться значения параметров.  Дополнительные сведения см. в разделе [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Однако если требуется использовать `<#@parameter>` в шаблоне времени выполнения, можно передать ему значения с помощью словаря сеанса.  Для примера предположим, что создан предварительно обработанный шаблон \(файл\) с именем `PreTextTemplate1`.  Можно вызвать шаблон в программе с использованием следующего кода.  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## Получение аргументов из служебной программы TextTemplate.exe  
  
> [!IMPORTANT]
>  Директива `parameter` не извлекает значения, заданные в параметре `–a` служебной программы `TextTransform.exe`.  Чтобы получить эти значения, задайте значение `hostSpecific="true"` в директиве `template` и воспользуйтесь командой `this.Host.ResolveParameterValue("","","argName")`.