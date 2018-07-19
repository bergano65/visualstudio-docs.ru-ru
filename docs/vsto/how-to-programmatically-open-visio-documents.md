---
title: 'Как: открытие документов Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3a7d2a9855abef0415661798c8a213eb748e22f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257856"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Как: открытие документов Visio
  Существует два метода для открытия существующих документов Microsoft Office Visio: открытие и OpenEx. Метод OpenEx идентична метод Open, за исключением того, что предоставляет аргументы, в которых вызывающий может указать параметры открытия документа.  
  
 Подробные сведения об объектной модели см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) и метода [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) .  
  
## <a name="open-a-visio-document"></a>Открытие документа Visio  
  
### <a name="to-open-a-visio-document"></a>Открытие документа Visio  
  
-   Вызовите `Microsoft.Office.Interop.Visio.Documents.Open` метод и укажите полный путь к документу Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Открытие документа Visio с заданными аргументами  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Открытие документа Visio как закрепленного и доступного только для чтения  
  
-   Вызовите `Microsoft.Office.Interop.Visio.Documents.OpenEx` метод, укажите полный путь к документу Visio и включите аргументы, которые вы хотите использовать — в данном случае Docked и только для чтения.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Практическое: программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Практическое: программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое: программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое: программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  