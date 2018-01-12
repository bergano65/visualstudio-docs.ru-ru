---
title: "Как: Создание и изменение настраиваемых свойств документа | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5d081beb3422126f6ccf7484cb08e7fa43da8874
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Практическое руководство. Создание и изменение настраиваемых свойств документа
  Перечисленные выше приложения Microsoft Office предоставляют встроенные свойства, которые хранятся в документах. Кроме того, можно создавать и изменять настраиваемые свойства документа при наличии дополнительных сведений, которые необходимо хранить вместе с документом.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Свойство CustomDocumentProperties документа для работы с пользовательскими свойствами. Например, в проекте уровня документа для Microsoft Office Excel используйте свойство <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> класса `ThisWorkbook` . В проекте надстройки VSTO для Excel используйте свойство <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Excel.Workbook> . Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties> , который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty> . Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.  
  
 В следующем примере показано, как добавить пользовательское свойство в настройку уровня документа для Excel и присвоить ему значение.  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как: доступ к настраиваемым свойствам и работа документа в Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Пример  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При попытке доступа к свойству `Value` для неопределенного свойства возникает исключение.  
  
## <a name="see-also"></a>См. также  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [Практическое руководство. Чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  