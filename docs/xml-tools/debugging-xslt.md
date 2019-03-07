---
title: Способы отладки XSLT-коде
ms.date: 03/05/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 23e108e476bfa9cb3ce699a16c77eb3520ed4785
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526390"
---
# <a name="debugging-xslt"></a>Отладка XSLT

Можно выполнять отладку кода XSLT в Visual Studio. XSLT отладчик поддерживает задание точек останова, просмотр состояний выполнения XSLT и т. д. Отладчик XSLT можно использовать для отладки таблицы стилей XSLT или приложения XSLT.

Можно выполнить код по одной строке за раз с заходом, шаг с обходом или шаг с выходом. Команды для использования возможностей пошагового прохождения кода отладчика XSLT, что такие же, как для Visual Studio отладчиков.

При запуске отладки отладчик XSLT открывает окна, в которых отображается входной документ и выход XSLT.

> [!NOTE]
> Отладчик XSLT доступен только в выпуске Visual Studio Enterprise.

## <a name="debug-from-the-xml-editor"></a>Отладка в редакторе XML

Отладчик можно запустить при наличии таблицы стилей или входной XML-файл открыт в редакторе. Это позволяет отлаживать при создании стилей.

1. Откройте таблицу стилей или XML-файл в Visual Studio.

1. Выберите **начать отладку XSLT** из **XML** меню или нажмите клавишу **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Отладка из приложения, использующего XSLT

Можно выполнить пошаговую отладку XSLT при отладке приложения. При нажатии клавиши **F11** на <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> вызовов, отладчик может войти в код XSLT.

> [!NOTE]
> Выполнение шага со входом в код XSLT из класса <xref:System.Xml.Xsl.XslTransform> не поддерживается. Класс <xref:System.Xml.Xsl.XslCompiledTransform> является единственным обработчиком XSLT, поддерживающим вход в код XSLT при отладке.

### <a name="to-start-debugging-an-xslt-application"></a>Начало отладки приложения XSLT

1. При создании объекта <xref:System.Xml.Xsl.XslCompiledTransform> устанавливайте в своем коде параметр `enableDebug` в значение `true`. Это заставляет обработчик XSLT создавать отладочные данные при компиляции кода.

1. Нажмите клавишу **F11** на шаг с заходом в код XSLT.

   Таблица стилей XSLT загружается в новом окне документа и запускается отладчик XSLT.

   Можно также добавить точку останова в таблицу стилей и запустить приложение.

### <a name="example"></a>Пример

Ниже приведен пример программы C# XSLT. Он показывает, как включить отладку XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Профилировщик XSLT

[Профилировщик XSLT](../xml-tools/xslt-profiler.md) — это средство, которое позволяет разработчикам измерять, оценивать и исправлять проблемы, связанные с производительностью, в XSLT коде, создавая подробные отчеты о производительности XSLT. Дополнительные сведения см. в разделе [профилировщик XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>См. также

- [Пошаговое руководство: Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Первое знакомство с помощью отладчика Visual Studio](../debugger/debugger-feature-tour.md)
- [Общие сведения об отладке: Точки останова](../debugger/using-breakpoints.md)