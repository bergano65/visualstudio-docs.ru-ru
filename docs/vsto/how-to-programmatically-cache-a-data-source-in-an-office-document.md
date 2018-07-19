---
title: 'Практическое: программное кэширование источника данных в документах Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89aef81c68b95947215142ddadf9081d49aa95b2
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256709"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Практическое: программное кэширование источника данных в документах Office
  Можно программно добавить объект данных в кэш данных в документе путем вызова `StartCaching` метода ведущего элемента, такого как <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, или <xref:Microsoft.Office.Tools.Excel.Worksheet>. Удаляет объект данных из кэша данных, вызвав `StopCaching` метод ведущего элемента.  
  
 `StartCaching` Метод и `StopCaching` метод являются частными, но они отображаются в IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 При использовании `StartCaching` метод, чтобы добавить объект данных в кэш данных, объект данных не должны быть объявлены с <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибута. Тем не менее объект данных должен соответствовать определенным требованиям, добавляемый в кэш данных. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).  
  
## <a name="to-programmatically-cache-a-data-object"></a>Объект данных в кэш программным образом  
  
1.  Объявите объект данных на уровне класса, а не внутри метода. В этом примере предполагается, что вы объявляете <xref:System.Data.DataSet> с именем `dataSet1` , необходимо поместить в кэш программным способом.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Создайте экземпляр объекта данных, а затем вызовите `StartCaching` метод экземпляра документа или листа и передайте имя объекта данных.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
## <a name="to-stop-caching-a-data-object"></a>Для прекращения кэширования объекта данных  
  
1.  Вызовите `StopCaching` метод экземпляра документа или листа и передайте имя объекта данных. В этом примере предполагается, что у вас есть <xref:System.Data.DataSet> с именем `dataSet1` , вы хотите остановить кэширование.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Не вызывайте `StopCaching` из обработчика событий для `Shutdown` события документа или листа. К моменту `Shutdown` события, уже слишком поздно для изменения кэша данных. Дополнительные сведения о `Shutdown` событий, см. в разделе [события в проектах Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>См. также  
 [Кэширование данных](../vsto/caching-data.md)   
 [Практическое: кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Практическое: кэшировать данные в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Сохранение данных](/visualstudio/data-tools/saving-data)  
  
  