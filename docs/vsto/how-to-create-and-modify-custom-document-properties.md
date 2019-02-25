---
title: Практическое руководство. Создание и изменение настраиваемых свойств документа
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5747c4c530a358b5ca25b30aaadbe57c10c000c2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600884"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Практическое руководство. Создание и изменение настраиваемых свойств документа
  Перечисленные выше приложения Microsoft Office предоставляют встроенные свойства, которые хранятся в документах. Кроме того, можно создавать и изменять настраиваемые свойства документа при наличии дополнительных сведений, которые необходимо хранить вместе с документом.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Используйте свойство CustomDocumentProperties документа для работы с пользовательскими свойствами. Например, в проекте уровня документа для Microsoft Office Excel используйте свойство <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> класса `ThisWorkbook` . В проекте надстройки VSTO для Excel используйте свойство <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Excel.Workbook> . Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties> , который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty> . Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.

 В следующем примере показано, как добавить пользовательское свойство в настройку уровня документа для Excel и присвоить ему значение.

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Доступ и использовать настраиваемые свойства документа в Microsoft Word? ](http://go.microsoft.com/fwlink/?LinkId=136772).

## <a name="example"></a>Пример
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Отказоустойчивость
 При попытке доступа к свойству `Value` для неопределенного свойства возникает исключение.

## <a name="see-also"></a>См. также
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)
- [Практическое руководство. Чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md)
