---
title: Обработка текстовых шаблонов с помощью пользовательского хост-класса
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f7ecd6508df780f570d10b3d615094fae15209d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591688"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Обработка текстовых шаблонов с помощью пользовательского основного приложения

Процесс *преобразования текстовых шаблонов* принимает текстовый файл *шаблона* в качестве входных данных и создает текстовый файл в качестве выходных данных. Модуль преобразования текста можно вызвать из расширения Visual Studio или из автономного приложения, работающего на компьютере, на котором установлена программа Visual Studio. Однако необходимо предоставить *узел текстовых шаблонов*. Этот класс подключает шаблон к среде, находя ресурсы, такие как сборки и включаемые файлы, и работает с выводом и сообщениями об ошибках.

> [!TIP]
> Если вы пишете пакет или расширение, которое будет выполняться в Visual Studio, рассмотрите возможность использования службы текстовых шаблонов вместо написания собственного узла. Дополнительные сведения см. [в разделе вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Преобразования текстовых шаблонов не рекомендуется использовать в серверных приложениях. Преобразования текстовых шаблонов не рекомендуется использовать, когда выполняется более одного потока. Это объясняется тем, что модуль текстовых шаблонов многократно использует один домен приложения для преобразования, компиляции и выполнения шаблонов. Потокобезопасность преобразованного кода не предусмотрена. Механизм предназначен для обработки файлов последовательно, так как они находятся в проекте Visual Studio во время разработки.
>
> Для приложений времени выполнения рассмотрите возможность использования предварительно обработанных текстовых шаблонов: см. статью [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Если приложение использует набор шаблонов, фиксированных во время выполнения, проще использовать предварительно преобразованные текстовые шаблоны. Этот подход также можно использовать, если приложение будет выполняться на компьютере, на котором не установлен Visual Studio. Дополнительные сведения см. [в разделе Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Выполнение текстового шаблона в приложении

Для выполнения текстового шаблона следует вызвать метод ProcessTemplate класса <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Приложение должно найти и предоставить этот шаблон, а также принять вывод.

 В параметре `host` необходимо предоставить класс, реализующий [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Он вызывается процессором шаблонов.

 Основное приложение должно быть способно протоколировать ошибки, разрешать ссылки на сборки и включаемые файлы. предоставлять домен приложения, в котором может выполняться шаблон, и вызывать подходящий процессор для каждой директивы.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> определяется в **Microsoft. VisualStudio. TextTemplating.\*0. dll**, а [Итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) определяется в **Microsoft. VisualStudio. TextTemplating. interfaces.\*. 0. dll**.

## <a name="in-this-section"></a>в этом разделе
 [Пошаговое руководство: Создание пользовательского узла текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md) показывает, как создать узел пользовательского текстового шаблона, который делает функциональность текстового шаблона доступной вне Visual Studio.

## <a name="reference"></a>Ссылка
 [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Связанные разделы

- [Процесс преобразования текстовых шаблонов](../modeling/the-text-template-transformation-process.md) описывает, как работает преобразование текста и какие части можно настраивать.
- [Создание пользовательских обработчиков директив текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md) предоставляет общие сведения о процессорах директив текстовых шаблонов.
