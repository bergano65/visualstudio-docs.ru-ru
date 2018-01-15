---
title: "Обработка текстовых шаблонов с помощью пользовательского хост | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d3eabfb846b6b488c99202037ebea90c4f9f04db
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Обработка текстовых шаблонов с помощью пользовательского хост-класса
*Преобразования текстового шаблона* обработки принимает *текстового шаблона* файл в качестве входных данных и создает текстовый файл на выходе. Можно вызывать процессор преобразования текста из расширения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или из отдельного приложения, которые выполняется на компьютере, на котором установлена [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Тем не менее, необходимо предоставить *приложение преобразования текстового шаблона*. Этот класс подключает шаблон к среде, находя ресурсы, такие как сборки и включаемые файлы, и работает с выводом и сообщениями об ошибках.  
  
> [!TIP]
>  При создании пакета или расширения, который будет выполняться в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно воспользоваться службой текстовых шаблонов, а не создавать собственный узел. Дополнительные сведения см. в разделе [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Преобразования текстовых шаблонов не рекомендуется использовать в серверных приложениях. Преобразования текстовых шаблонов не рекомендуется использовать, когда выполняется более одного потока. Это объясняется тем, что модуль текстовых шаблонов многократно использует один домен приложения для преобразования, компиляции и выполнения шаблонов. Потокобезопасность преобразованного кода не предусмотрена. Модуль предназначен для серийной обработки файлов, поскольку они находятся в проекте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] во время разработки.  
>   
>  Для выполнения приложений, рассмотрите возможность использования предварительно обработанных текстовых шаблонах: в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Если приложение использует набор шаблонов, фиксированных во время выполнения, проще использовать предварительно преобразованные текстовые шаблоны. Данный подход можно также использовать в случае, когда приложение будет выполняться на компьютере, где не установлена [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="executing-a-text-template-in-your-application"></a>Выполнение текстового шаблона в приложении  
 Для выполнения текстового шаблона следует вызвать метод ProcessTemplate класса <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 Приложение должно найти и предоставить этот шаблон, а также принять вывод.  
  
 В параметре `host` задается класс, реализующий интерфейс <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Он вызывается процессором шаблонов.  
  
 ведущее приложение должно быть способно протоколировать ошибки, разрешать ссылки на сборки и включаемые файлы. предоставлять домен приложения, в котором может выполняться шаблон, и вызывать подходящий процессор для каждой директивы.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>определен в **Microsoft.VisualStudio.TextTemplating.\*. 0. библиотека dll**, и <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> определяется в **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0. библиотека dll**.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пошаговое руководство. Создание пользовательского хост-класса для текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Показано, как создать основное приложение текстового шаблона, которое делает функциональные возможности текстовых шаблонов доступными вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>Связанные разделы  
 [Процесс преобразования текстового шаблона](../modeling/the-text-template-transformation-process.md)  
 Описано, как работает преобразование текста и какие части можно настраивать.  
  
 [Создание пользовательских обработчиков директив для текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Предоставляется обзор процессоров директив текстовых шаблонов.