---
title: "Как: программное кэширование источника данных в документ Office | Документы Microsoft"
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
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09d4b46aaa68a92ffb9ddfe70f329e97a1b7526d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Практическое руководство. Программное кэширование источника данных в документе MS Office.
  Программно добавить объект данных в кэш данных в документе путем вызова `StartCaching` метода ведущего элемента, такого как <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, или <xref:Microsoft.Office.Tools.Excel.Worksheet>. Удаляет объект данных из кэша данных, вызвав `StopCaching` метод ведущего элемента.  
  
 `StartCaching` Метод и `StopCaching` метод являются частными, но они отображаются в IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 При использовании `StartCaching` метод, чтобы добавить объект данных в кэш данных, объект данных не должны быть объявлены с <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибута. Однако объект данных необходимо выполнить определенные требования для добавления в кэш данных. Для получения дополнительной информации см. [Caching Data](../vsto/caching-data.md).  
  
### <a name="to-programmatically-cache-a-data-object"></a>Объект данных в кэш программным образом  
  
1.  Объявите объект данных на уровне класса, а не внутри метода. В этом примере предполагается, что вы объявляете <xref:System.Data.DataSet> с именем `dataSet1` , необходимо поместить в кэш программным образом.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Обработайте объект данных, а затем вызвать `StartCaching` метод экземпляра документа или листа и передайте имя объекта данных.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>Для прекращения кэширования объекта данных  
  
1.  Вызовите `StopCaching` метод экземпляра документа или листа и передайте имя объекта данных. В этом примере предполагается, что <xref:System.Data.DataSet> с именем `dataSet1` , которую требуется остановить кэширование.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Не вызывайте `StopCaching` из обработчика событий для `Shutdown` события документа или листа. К моменту `Shutdown` событие, он слишком поздно изменять кэш данных. Дополнительные сведения о `Shutdown` событий, в разделе [события в проектах Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>См. также  
 [Кэширование данных](../vsto/caching-data.md)   
 [Как: кэширование данных для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Как: кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Сохранение данных](/visualstudio/data-tools/saving-data)  
  
  