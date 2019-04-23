---
title: Практическое руководство. Кэширование данных в документе, защищенном паролем
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c231aac3b78ddb5100cc06600059045fdc463e51
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074012"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Практическое руководство. Кэширование данных в документе, защищенном паролем
  При добавлении данных в кэш данных в документе или книге, защищенной паролем, изменения в кэшированные данные не сохраняются автоматически. Можно сохранить изменения в кэшированных данных путем переопределения двух методов в проекте.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Кэширование в документах Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Кэширование данных в документ Word, защищенным паролем

1. В `ThisDocument` класса, пометьте открытое поле или свойство, должен быть помещен в кэш. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).

2. Переопределить <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> метод в `ThisDocument` класса и снять защиту с документа.

     При сохранении документа, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту документа. В результате изменения кэшированных данных для сохранения.

3. Переопределить <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> метод в `ThisDocument` класса и повторно применить защиту к документу.

     После сохранения документа [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность повторно применить защиту к документу.

### <a name="example"></a>Пример
 В следующем примере кода показано, как кэшировать данные в документ Word, защищенным паролем. Прежде чем код удаляет защиту в <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> метод, он сохраняет текущие <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> значение таким образом, чтобы повторно применить тот же тип защиты в <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> метод.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Компиляция кода
 Добавьте следующий код в `ThisDocument` в своем проекте. Этот код предполагает, что пароль хранится в поле с именем `securelyStoredPassword`.

## <a name="cache-in-excel-workbooks"></a>Кэширование в книгах Excel
 В проектах Excel, эта процедура необходима только в том случае, при защите всей книги с помощью пароля с помощью <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> метод. Эта процедура не является обязательным, если защитить только один лист с помощью пароля с помощью <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> метод.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Для кэширования данных в книге Excel, который защищен с помощью пароля

1. В `ThisWorkbook` класс или один из `Sheet` *n* классы, пометьте открытое поле или свойство, должен быть помещен в кэш. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).

2. Переопределить <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> метод в `ThisWorkbook` класса и снять защиту с книги.

     При сохранении книги [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту книги. В результате изменения кэшированных данных для сохранения.

3. Переопределить <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> метод в `ThisWorkbook` класса и повторно применить защиту к документу.

     После сохранения книги [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность повторно применить защиту к книге.

### <a name="example"></a>Пример
 В следующем примере кода показано, как кэшировать данные в книге Excel, который защищен паролем. Прежде чем код удаляет защиту в <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> метод, он сохраняет текущие <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> и <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> значения, таким образом, чтобы повторно применить тот же тип защиты в <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> метод.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Компиляция кода
 Добавьте следующий код в `ThisWorkbook` в своем проекте. Этот код предполагает, что пароль хранится в поле с именем `securelyStoredPassword`.

## <a name="see-also"></a>См. также
- [Кэширование данных](../vsto/caching-data.md)
- [Практическое руководство. Кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Практическое руководство. Программное кэширование источника данных в документах Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
