---
title: 'Практическое: чтение из и запись в свойства документа'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: de9ae85156f9d272901893c74c5d2c9729a0a3dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924232"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Практическое: чтение из и запись в свойства документа
  Свойства документа можно сохранять вместе с документом. Приложения Office содержат различные встроенные свойства, например автора, название и тему. В этом разделе показано, как задать свойства документа в Microsoft Office Excel и Microsoft Office Word.  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [как I: доступа и управления настраиваемых свойств документа в Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="set-document-properties-in-excel"></a>Набор свойств документа в Excel  
 Для работы со встроенными свойствами в Excel используйте следующие свойства.  
  
- В проекте на уровне документа используйте свойство <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> класса `ThisWorkbook` .  
  
- В проекте надстройки VSTO используйте свойство <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Excel.Workbook> .  
  
  Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties> , который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty> . Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.  
  
  В следующем примере кода показано, как изменить встроенное свойство **Revision Number** в проекте на уровне документа.  
  
### <a name="to-change-the-revision-number-property-in-excel"></a>Изменение свойства «Номер редакции» в Excel  
  
1.  Назначьте переменной встроенные свойства документа.  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  Увеличьте значение свойства `Revision Number` на единицу.  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="set-document-properties-in-word"></a>Набор свойств документа в Word  
 Для работы со встроенными свойствами в Word используйте следующие свойства.  
  
- В проекте на уровне документа используйте свойство <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> класса `ThisDocument` .  
  
- В проекте надстройки VSTO используйте свойство <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Word.Document> .  
  
  Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties> , который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty> . Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.  
  
  В следующем примере кода показано, как изменить встроенное свойство **Subject** в проекте на уровне документа.  
  
### <a name="to-change-the-subject-property"></a>Изменение свойства темы  
  
1.  Назначьте переменной встроенные свойства документа.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  Измените значение свойства `Subject` на «Техническая документация».  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 В примерах предполагается, что код написан в классе `ThisWorkbook` в проекте на уровне документа для Excel и в классе `ThisDocument` в проекте на уровне документа для Word.  
  
 Несмотря на то что вы работаете с Word и Excel и их объектами, Microsoft Office предоставляет список доступных встроенных свойств документа. В случае попытки доступа к неопределенному свойству возникает исключение.  
  
## <a name="see-also"></a>См. также  
 [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)   
 [Практическое: Создание и изменение настраиваемых свойств документа](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  