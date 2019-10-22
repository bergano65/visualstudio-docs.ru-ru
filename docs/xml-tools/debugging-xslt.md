---
title: Способы отладки кода XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: bb358efb711211d58525afb8d30d5cb4cad6b2e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646070"
---
# <a name="debugging-xslt"></a>Отладка XSLT

Код XSLT можно отлаживать в Visual Studio. Отладчик XSLT поддерживает задание точек останова, Просмотр состояний выполнения XSLT и т. д. Отладчик XSLT можно использовать для отладки таблиц стилей XSLT или XSLT-приложений.

Можно выполнить код по одной строке за раз, пошаговым выполнением, пошаговым выполнением или выходом из кода. Команды для использования функций обработки кода отладчика XSLT аналогичны командам для других отладчиков Visual Studio.

При запуске отладки отладчик XSLT открывает окна, в которых отображается входной документ и выход XSLT.

> [!NOTE]
> Отладчик XSLT доступен только в выпусках Visual Studio Professional и Enterprise.

## <a name="debug-from-the-xml-editor"></a>Отладка из редактора XML

Отладчик можно запустить при наличии таблицы стилей или входного XML-файла, открытого в редакторе. Это позволяет выполнять отладку по мере разработки таблицы стилей.

1. Откройте таблицу стилей или XML-файл в Visual Studio.

1. Выберите **запустить отладку XSLT** в меню **XML** или нажмите клавишу **ALT** +**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Отладка из приложения, использующего XSLT

При отладке приложения можно выполнить шаг с заходом в XSLT. При нажатии клавиши **F11** при вызове <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> отладчик может выполнить шаг с заходом в код XSLT.

> [!NOTE]
> Выполнение шага со входом в код XSLT из класса <xref:System.Xml.Xsl.XslTransform> не поддерживается. Класс <xref:System.Xml.Xsl.XslCompiledTransform> является единственным обработчиком XSLT, поддерживающим вход в код XSLT при отладке.

### <a name="to-start-debugging-an-xslt-application"></a>Начало отладки приложения XSLT

1. При создании объекта <xref:System.Xml.Xsl.XslCompiledTransform> устанавливайте в своем коде параметр `enableDebug` в значение `true`. Это заставляет обработчик XSLT создавать отладочные данные при компиляции кода.

1. Нажмите клавишу **F11** , чтобы выполнить шаг с заходом в код XSLT.

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

[Профилировщик XSLT](../xml-tools/xslt-profiler.md) — это средство, которое позволяет разработчикам измерять, оценивать и нацелить проблемы производительности в коде XSLT, создавая подробные отчеты о производительности XSLT. Дополнительные сведения см. в статье [Профилировщик XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>См. также

- [Пошаговое руководство. Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Знакомство с отладчиком Visual Studio](../debugger/debugger-feature-tour.md)
- [Основы отладки: точки останова](../debugger/using-breakpoints.md)
