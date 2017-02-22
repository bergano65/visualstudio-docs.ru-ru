---
title: "Processing Text Templates by using a Custom Host | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, in application or VS extension"
  - "text templates, custom directive hosts"
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 33
caps.handback.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Processing Text Templates by using a Custom Host
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Процесс преобразования текстового шаблона* принимает файл *текстового шаблона* на входе и создает текстовый файл на выходе.  Можно вызывать процессор преобразования текста из расширения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или из отдельного приложения, которые выполняется на компьютере, на котором установлена [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Однако необходимо предоставить *основное приложение преобразования текстового шаблона*.  Этот класс подключает шаблон к среде, находя ресурсы, такие как сборки и включаемые файлы, и работает с выводом и сообщениями об ошибках.  
  
> [!TIP]
>  При создании пакета или расширения, который будет выполняться в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно воспользоваться службой текстовых шаблонов, а не создавать собственный узел.  Дополнительные сведения см. в разделе [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Преобразования текстовых шаблонов не рекомендуется использовать в серверных приложениях.  Преобразования текстовых шаблонов не рекомендуется использовать, когда выполняется более одного потока.  Это объясняется тем, что модуль текстовых шаблонов многократно использует один домен приложения для преобразования, компиляции и выполнения шаблонов.  Потокобезопасность преобразованного кода не предусмотрена.  Модуль предназначен для серийной обработки файлов, поскольку они находятся в проекте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] во время разработки.  
>   
>  При работе с приложениями времени выполнения имеет смысл использовать предварительно обработанные текстовые шаблоны. См. раздел [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Если приложение использует набор шаблонов, фиксированных во время выполнения, проще использовать предварительно преобразованные текстовые шаблоны.  Данный подход можно также использовать в случае, когда приложение будет выполняться на компьютере, где не установлена [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Дополнительные сведения см. в разделе [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Выполнение текстового шаблона в приложении  
 Для выполнения текстового шаблона следует вызвать метод ProcessTemplate класса <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 Приложение должно найти и предоставить этот шаблон, а также принять вывод.  
  
 В параметре `host` задается класс, реализующий интерфейс <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.  Он вызывается процессором шаблонов.  
  
 Основное приложение должно быть способно протоколировать ошибки, разрешать ссылки на сборки и включаемые файлы. предоставлять домен приложения, в котором может выполняться шаблон, и вызывать подходящий процессор для каждой директивы.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> определяется в **Microsoft.VisualStudio.TextTemplating.\*.0.dll**, а <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> определяется в **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0.dll**.  
  
## В данном разделе  
 [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Показано, как создать основное приложение текстового шаблона, которое делает функциональные возможности текстовых шаблонов доступными вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Ссылка  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## См. также  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Описано, как работает преобразование текста и какие части можно настраивать.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Предоставляется обзор процессоров директив текстовых шаблонов.