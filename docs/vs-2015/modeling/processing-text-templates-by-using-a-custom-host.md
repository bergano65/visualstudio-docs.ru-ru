---
title: Обработка текстовых шаблонов с помощью пользовательского хост | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5fa54f6b7ea57b6374e8fef291c64f0e5369ffea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303463"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Обработка текстовых шаблонов с помощью пользовательского хост-класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Преобразования текстового шаблона* обработки принимает *текстового шаблона* файл на входе и создает текстовый файл на выходе. Можно вызывать процессор преобразования текста из расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] или из отдельного приложения, которые выполняется на компьютере, на котором установлена [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Тем не менее, необходимо предоставить *основное приложение текстовых шаблонов*. Этот класс подключает шаблон к среде, находя ресурсы, такие как сборки и включаемые файлы, и работает с выводом и сообщениями об ошибках.  
  
> [!TIP]
>  При создании пакета или расширения, который будет выполняться в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно воспользоваться службой текстовых шаблонов, а не создавать собственный узел. Дополнительные сведения см. в разделе [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Преобразования текстовых шаблонов не рекомендуется использовать в серверных приложениях. Преобразования текстовых шаблонов не рекомендуется использовать, когда выполняется более одного потока. Это объясняется тем, что модуль текстовых шаблонов многократно использует один домен приложения для преобразования, компиляции и выполнения шаблонов. Потокобезопасность преобразованного кода не предусмотрена. Модуль предназначен для серийной обработки файлов, поскольку они находятся в проекте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] во время разработки.  
>   
>  Для выполнения приложений, рассмотрите возможность использования предварительно обработанных текстовых шаблонах: см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Если приложение использует набор шаблонов, фиксированных во время выполнения, проще использовать предварительно преобразованные текстовые шаблоны. Данный подход можно также использовать в случае, когда приложение будет выполняться на компьютере, где не установлена [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
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
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> определяется в **Microsoft.VisualStudio.TextTemplating.\*. 0. библиотека dll**, и <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> определяется в **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0. библиотека dll**.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пошаговое руководство. Создание пользовательского хост-класса для текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Показано, как создать ведущее приложение текстового шаблона, которое делает функциональные возможности текстовых шаблонов доступными вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>Связанные разделы  
 [Процесс преобразования текстового шаблона](../modeling/the-text-template-transformation-process.md)  
 Описано, как работает преобразование текста и какие части можно настраивать.  
  
 [Создание пользовательских обработчиков директив для текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Предоставляется обзор процессоров директив текстовых шаблонов.



