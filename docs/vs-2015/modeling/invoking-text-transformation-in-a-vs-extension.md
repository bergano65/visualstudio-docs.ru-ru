---
title: Вызов преобразования текста в расширении VS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a87f84a945d9d79f6d481f7bcc9e656f7ec7bcbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646151"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Вызов преобразования текста в расширении VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При написании [расширения Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14) , такого как команда меню или [доменный язык](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), можно использовать службу текстовых шаблонов для преобразования текстовых шаблонов. Получите службу [стексттемплатинг](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) и приведите ее к [итексттемплатинг](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="getting-the-text-templating-service"></a>Получение службы текстовых шаблонов

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));

```

## <a name="passing-parameters-to-the-template"></a>Передача параметров в шаблоны
 Параметры можно передавать в шаблон. Чтобы получить значения параметров в шаблоне, можно воспользоваться директивой `<#@parameter#>`.

 Для этого типа параметра необходимо использовать сериализуемый или маршалируемый тип. Это значит, что тип должен объявляться с типом <xref:System.SerializableAttribute> или наследоваться от типа <xref:System.MarshalByRefObject>. Это ограничение является обязательным, потому что текстовый шаблон выполняется в отдельном домене приложения. Все встроенные типы, такие как **System. String** и **System. Int32** , являются сериализуемыми.

 Для передачи значений параметров вызывающий код может размещать значения либо в словаре `Session`, либо в типе <xref:System.Runtime.Remoting.Messaging.CallContext>.

 В следующем примере оба метода использованы для преобразования короткого тестового шаблона:

```
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
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
 Любые ошибки, возникающие в процессе обработки, отображаются в окне ошибок [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Кроме того, можно получать уведомления об ошибках, указывая обратный вызов, который реализует [итексттемплатингкаллбакк](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

 Если необходимо записать строку результатов в файл, полезно знать, какие расширение файла и кодировка были заданы в директиве `<#@output#>` шаблона. Эти сведения также передаются обратному вызову. Дополнительные сведения см. в разделе [директива вывода T4](../modeling/t4-output-directive.md).

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

 Предупреждение компилятора отображается в окне ошибок [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и создает вызов `ErrorCallback`.

## <a name="reference-parameters"></a>Параметры ссылок
 Можно передавать значения из текстового шаблона, используя класс параметров, наследуемый от <xref:System.MarshalByRefObject>.

## <a name="related-topics"></a>См. также
 Чтобы создать текст из предварительно обработанного текстового шаблона, вызовите метод `TransformText()` созданного класса. Дополнительные сведения см. [в разделе Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Для создания текста вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ного расширения: определите пользовательский узел. Дополнительные сведения см. [в разделе Обработка текстовых шаблонов с помощью пользовательского узла](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Для создания исходного кода, который впоследствии может быть скомпилирован и выполнен: вызовите метод [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) объекта [итексттемплатинг](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).
