---
title: Обработка текстовых шаблонов с помощью пользовательского узла | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71f18fbbf9f2d5c587c2cd0961c6625467f4f298
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652456"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Обработка текстовых шаблонов с помощью пользовательского хост-класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Процесс *преобразования текстовых шаблонов* принимает текстовый файл *шаблона* в качестве входных данных и создает текстовый файл в качестве выходных данных. Можно вызывать процессор преобразования текста из расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] или из отдельного приложения, которые выполняется на компьютере, на котором установлена [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Однако необходимо предоставить *узел текстовых шаблонов*. Этот класс подключает шаблон к среде, находя ресурсы, такие как сборки и включаемые файлы, и работает с выводом и сообщениями об ошибках.

> [!TIP]
> При создании пакета или расширения, который будет выполняться в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно воспользоваться службой текстовых шаблонов, а не создавать собственный узел. Дополнительные сведения см. [в разделе вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Преобразования текстовых шаблонов не рекомендуется использовать в серверных приложениях. Преобразования текстовых шаблонов не рекомендуется использовать, когда выполняется более одного потока. Это объясняется тем, что модуль текстовых шаблонов многократно использует один домен приложения для преобразования, компиляции и выполнения шаблонов. Потокобезопасность преобразованного кода не предусмотрена. Модуль предназначен для серийной обработки файлов, поскольку они находятся в проекте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] во время разработки.
>
> Для приложений времени выполнения рассмотрите возможность использования предварительно обработанных текстовых шаблонов: см. статью [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Если приложение использует набор шаблонов, фиксированных во время выполнения, проще использовать предварительно преобразованные текстовые шаблоны. Данный подход можно также использовать в случае, когда приложение будет выполняться на компьютере, где не установлена [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. [в разделе Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="executing-a-text-template-in-your-application"></a>Выполнение текстового шаблона в приложении
 Для выполнения текстового шаблона следует вызвать метод ProcessTemplate класса <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Приложение должно найти и предоставить этот шаблон, а также принять вывод.

 В `host` параметре необходимо предоставить класс, реализующий [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Он вызывается процессором шаблонов.

 Основное приложение должно быть способно протоколировать ошибки, разрешать ссылки на сборки и включаемые файлы. предоставлять домен приложения, в котором может выполняться шаблон, и вызывать подходящий процессор для каждой директивы.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> определяется в **Microsoft. VisualStudio. TextTemplating. \*.0.dll**, а [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) определяется в **Microsoft. VisualStudio. TextTemplating. interfaces. \*.0.dll**.

## <a name="in-this-section"></a>в этом разделе
 [Пошаговое руководство. Создание узла пользовательского текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md) Показывает, как создать узел пользовательского текстового шаблона, который делает функциональность текстового шаблона доступной вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="reference"></a>Справочник
 [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>См. также
 [Процесс преобразования текстовых шаблонов](../modeling/the-text-template-transformation-process.md) Описывает, как работает преобразование текста и какие части можно настраивать.

 [Создание пользовательских обработчиков директив текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Содержит общие сведения о процессорах директив текстовых шаблонов.
