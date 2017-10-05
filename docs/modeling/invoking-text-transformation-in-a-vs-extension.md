---
title: "Вызов преобразования текста в расширении VS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 5
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f47e551fc1aff5e2e1c65ac80e9a020c28cee8dd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Вызов преобразования текста в расширении VS
При создании расширения Visual Studio, такого как команда меню или [доменного языка](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), службой текстовых шаблонов можно использовать для преобразования текстовых шаблонов. Получите службу типа <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> и выполните приведение к типу <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.  
  
## <a name="getting-the-text-templating-service"></a>Получение службы текстовых шаблонов  
  
```csharp  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
  
// Process a text template:  
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));  
  
```  
  
## <a name="passing-parameters-to-the-template"></a>Передача параметров в шаблоны  
 Параметры можно передавать в шаблон. Чтобы получить значения параметров в шаблоне, можно воспользоваться директивой `<#@parameter#>`.  
  
 Для этого типа параметра необходимо использовать сериализуемый или маршалируемый тип. Это значит, что тип должен объявляться с типом <xref:System.SerializableAttribute> или наследоваться от типа <xref:System.MarshalByRefObject>. Это ограничение является обязательным, потому что текстовый шаблон выполняется в отдельном домене приложения. Все встроенные типы, такие как **System.String** и **System.Int32** являются сериализуемыми.  
  
 Для передачи значений параметров вызывающий код может размещать значения либо в словаре `Session`, либо в типе <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 В следующем примере оба метода использованы для преобразования короткого тестового шаблона:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = dte;   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;  
  
// Create a Session in which to pass parameters:  
sessionHost.Session = sessionHost.CreateSession();  
sessionHost.Session["parameter1"] = "Hello";  
sessionHost.Session["parameter2"] = DateTime.Now;  
  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);  
  
// Process a text template:  
string result = t4.ProcessTemplate("",  
   // This is the test template:  
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"  
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"  
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"  
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");  
  
// This test code yields a result similar to the following line:  
//     Test: Hello    07/06/2010 12:37:45    42  
  
```  
  
## <a name="error-reporting-and-the-output-directive"></a>Отчеты об ошибках и директива Output  
 Любые ошибки, возникающие в процессе обработки, отображаются в окне ошибок [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Кроме того, чтобы настроить уведомления об ошибках, можно задать обратный вызов, реализующий <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.  
  
 Если необходимо записать строку результатов в файл, полезно знать, какие расширение файла и кодировка были заданы в директиве `<#@output#>` шаблона. Эти сведения также передаются обратному вызову. Дополнительные сведения см. в разделе [директива Output T4](../modeling/t4-output-directive.md).  
  
```csharp  
void ProcessMyTemplate(string MyTemplateFile)  
{  
  string templateContent = File.ReadAllText(MyTemplateFile);  
  T4Callback cb = new T4Callback();  
  // Process a text template:  
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);  
  // If there was an output directive in the MyTemplateFile,  
  // then cb.SetFileExtension() will have been called.  
  // Determine the output file name:  
  string resultFileName =   
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),   
        Path.GetFileNameWithoutExtension(MyTemplateFile))   
      + cb.fileExtension;  
  // Write the processed output to file:  
  File.WriteAllText(resultFileName, result, cb.outputEncoding);  
  // Append any error messages:  
  if (cb.errorMessages.Count > 0)  
  {  
    File.AppendAllLines(resultFileName, cb.errorMessages);  
  }  
}  
  
class T4Callback : ITextTemplatingCallback  
{  
  public List<string> errorMessages = new List<string>();  
  public string fileExtension = ".txt";  
  public Encoding outputEncoding = Encoding.UTF8;  
  
  public void ErrorCallback(bool warning, string message, int line, int column)  
  { errorMessages.Add(message); }  
  
  public void SetFileExtension(string extension)  
  { fileExtension = extension; }  
  
  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)  
  { outputEncoding = encoding; }  
}  
  
```  
  
 Код можно протестировать с использованием файла шаблона, аналогичного следующему:  
  
```  
<#@output extension=".htm" encoding="ASCII"#>  
<# int unused;  // Compiler warning "unused variable"  
#>  
Sample text.  
```  
  
 Предупреждение компилятора отображается в окне ошибок [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и создает вызов `ErrorCallback`.  
  
## <a name="reference-parameters"></a>Параметры ссылок  
 Можно передавать значения из текстового шаблона, используя класс параметров, наследуемый от <xref:System.MarshalByRefObject>.  
  
## <a name="related-topics"></a>Связанные разделы  
 Создание текста из предварительно обработанного текстового шаблона  
 Вызовите метод `TransformText()` сгенерированного класса. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Создание текста за пределами расширения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Определите пользовательское ведущее приложение. Дополнительные сведения см. в разделе [обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 Создание исходного кода с возможностью последующей компиляции и выполнения  
 Вызовите метод `t4.PreprocessTemplate()` типа <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.

