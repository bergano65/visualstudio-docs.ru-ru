---
title: Обработка текстовых шаблонов с помощью пользовательского хост-класса
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e72b279d55cbe11f6232ff1f91c8fee443d9c283
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910940"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Обработка текстовых шаблонов с помощью пользовательского основного приложения

*Преобразования текстового шаблона* обработки принимает *текстового шаблона* файл на входе и создает текстовый файл на выходе. Можно вызвать обработчик преобразования текста из расширения Visual Studio или из отдельного приложения на компьютере, на котором установлена Visual Studio. Тем не менее, необходимо предоставить *основное приложение текстовых шаблонов*. Этот класс подключает шаблон к среде, находя ресурсы, такие как сборки и включаемые файлы, и работает с выводом и сообщениями об ошибках.

> [!TIP]
> При создании пакета или расширения, который будет выполняться в Visual Studio, рассмотрите возможность использования службы текстовых шаблонов, а не создавать собственный узел. Дополнительные сведения см. в разделе [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Преобразования текстовых шаблонов не рекомендуется использовать в серверных приложениях. Преобразования текстовых шаблонов не рекомендуется использовать, когда выполняется более одного потока. Это объясняется тем, что модуль текстовых шаблонов многократно использует один домен приложения для преобразования, компиляции и выполнения шаблонов. Потокобезопасность преобразованного кода не предусмотрена. Модуль предназначен для серийной обработки файлов, так как они находятся в проекте Visual Studio во время разработки.
>
> Для выполнения приложений, рассмотрите возможность использования предварительно обработанных текстовых шаблонах: см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Если приложение использует набор шаблонов, фиксированных во время выполнения, проще использовать предварительно преобразованные текстовые шаблоны. Этот подход можно использовать также в том случае, если приложение запускается на компьютере, на котором не установлена среда Visual Studio. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Выполнение текстового шаблона в приложении

Для выполнения текстового шаблона следует вызвать метод ProcessTemplate класса <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
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
 [Пошаговое руководство: Создание пользовательского хост текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md) показано, как создать основное приложение текстового шаблона, делающий функциональные возможности текстовых шаблонов доступными вне Visual Studio.

## <a name="reference"></a>Ссылка
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>Связанные разделы

- [Процесс преобразования текстового шаблона](../modeling/the-text-template-transformation-process.md) описано, как работает преобразование текста и какие части можно настраивать.
- [Создание обработчиков пользовательских T4 текстовых шаблонов директива](../modeling/creating-custom-t4-text-template-directive-processors.md) Обзор текста процессоры директив шаблона.