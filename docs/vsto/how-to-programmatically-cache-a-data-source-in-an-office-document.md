---
title: Кэширование источника данных в документе Office программным способом
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241ce42c2d411fdaf611f3a7f2b52eb40c8c32a2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189580"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Руководство. программный кэш источника данных в документе Office
  Можно программно добавить объект данных в кэш данных в документе, вызвав метод `StartCaching` ведущего элемента, например <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>или <xref:Microsoft.Office.Tools.Excel.Worksheet>. Удалите объект данных из кэша данных, вызвав метод `StopCaching` ведущего элемента.

 Метод `StartCaching` и метод `StopCaching` являются частными, но они отображаются в IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 При использовании метода `StartCaching` для добавления объекта данных в кэш данных не требуется объявлять объект данных с атрибутом <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Однако объект данных должен соответствовать определенным требованиям для добавления в кэш данных. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Кэширование объекта данных программными средствами

1. Объявите объект данных на уровне класса, а не внутри метода. В этом примере предполагается, что вы объявили <xref:System.Data.DataSet> с именем `dataSet1`, которые требуется кэшировать программно.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Создайте экземпляр объекта данных, а затем вызовите метод `StartCaching` экземпляра документа или листа и передайте имя объекта данных.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Отмена кэширования объекта данных

1. Вызовите метод `StopCaching` экземпляра документа или листа и передайте имя объекта данных. В этом примере предполагается, что у вас есть <xref:System.Data.DataSet> с именем `dataSet1`, для которого необходимо прерывать кэширование.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > Не вызывайте `StopCaching` из обработчика событий для события `Shutdown` документа или листа. К моменту возникновения события `Shutdown` это слишком поздно для изменения кэша данных. Дополнительные сведения о событии `Shutdown` см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>См. также

- [Кэширование данных](../vsto/caching-data.md)
- [Как кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Пошаговое руководство. кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)
- [Сохранение данных](../data-tools/save-data-back-to-the-database.md)
