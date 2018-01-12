---
title: "Как: запуск отладки XSLT | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.workload: multiple
ms.openlocfilehash: af95385a0d95f3f6edba3b5813d35103cd4e13f6
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-start-debugging-xslt"></a>Практическое руководство. Запуск отладки XSLT.
Для отладки таблицы стилей XSLT или приложения XSLT можно использовать отладчик XSLT. При отладке можно выполнять код по одной строке, делая шаг с входом, шаг с пропуском или шаг с выходом. Команды для использования возможностей пошагового прохождения кода аналогичны в отладчике XSLT и в других отладчиках Visual Studio. При запуске отладки отладчик XSLT открывает окна, в которых отображается входной документ и выход XSLT.  
  
## <a name="xml-editor"></a>XML-редактор  
 Отладчик можно запустить из редактора XML. Это позволяет выполнять отладку по мере создания таблицы стилей.  
  
#### <a name="to-start-debugging-from-a-style-sheet"></a>Запуск отладки из таблицы стилей  
  
1.  Откройте таблицу стиля в XML-редакторе.  
  
2.  Выберите **Отладка XSL** из **XML** меню.  
  
#### <a name="to-start-debugging-from-an-xml-input-document"></a>Начало отладки с входного XML-документа  
  
1.  Откройте XML-документ в XML-редакторе.  
  
2.  Выберите **Отладка XSL** из **XML** меню.  
  
## <a name="xslt-from-other-languages"></a>XSLT из других языков  
 При отладке приложения можно сделать шаг с входом в код XSLT. Если нажать клавишу F11 при вызове <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>, отладчик может войти в код XSLT.  
  
> [!NOTE]
>  Выполнение шага со входом в код XSLT из класса <xref:System.Xml.Xsl.XslTransform> не поддерживается. Класс <xref:System.Xml.Xsl.XslCompiledTransform> является единственным обработчиком XSLT, поддерживающим вход в код XSLT при отладке.  
  
#### <a name="to-start-debugging-an-xslt-application"></a>Начало отладки приложения XSLT  
  
1.  При создании объекта <xref:System.Xml.Xsl.XslCompiledTransform> устанавливайте в своем коде параметр `enableDebug` в значение `true`.  
  
     Это заставляет обработчик XSLT создавать отладочные данные при компиляции кода.  
  
2.  Нажмите клавишу F11, чтобы войти в код XSLT.   
  
     Таблица стилей XSLT загружается в новое окно документа и запускается XSLT-отладчик.  
  
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
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";  
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
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)   
 [Обзор пошагового выполнения кода](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9)