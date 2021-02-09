---
title: Как добавлять элементы управления "Диаграмма" на листы
description: Узнайте, как можно добавлять элементы управления диаграммы в Microsoft Office лист Excel во время разработки и во время выполнения в настройках уровня документа.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4fd82cf9d8d5cb15215bf7ecbfa51c735ef52a0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917387"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Как добавлять элементы управления "Диаграмма" на листы
  <xref:Microsoft.Office.Tools.Excel.Chart>Элементы управления можно добавлять в Microsoft Office лист Excel во время разработки и во время выполнения в настройках уровня документа. Элементы управления также можно добавлять <xref:Microsoft.Office.Tools.Excel.Chart> во время выполнения в надстройках VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В этом разделе описываются следующие задачи.

- [Добавление элементов управления диаграммы во время разработки](#designtime)

- [Добавление элементов управления диаграммы во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Добавление элементов управления диаграммы во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения об элементах <xref:Microsoft.Office.Tools.Excel.Chart> управления см. в разделе [элемент управления диаграммы](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Добавление элементов управления диаграммы во время разработки
 Для добавления элемента управления <xref:Microsoft.Office.Tools.Excel.Chart> на лист можно использовать ту же процедуру, что и для добавления диаграммы в приложении.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.Chart>Элемент управления недоступен на **панели элементов** или в окне **Источники данных** .

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Добавление элемента управления ведущего приложения «Диаграмма» на лист в Excel

1. На вкладке **Вставка** в группе **диаграммы** щелкните **столбец**, щелкните категорию диаграмм, а затем выберите нужный тип диаграммы.

2. В диалоговом окне **Вставка диаграммы** нажмите кнопку **ОК**.

3. На вкладке **конструктор** в группе **данные** нажмите кнопку **выбрать данные**.

4. В диалоговом окне **Выбор источника данных** щелкните поле **диапазон данных** **диаграммы** и отмените выбор по умолчанию.

5. На листе **данные для диаграммы** выберите диапазон ячеек, содержащих данные для диаграммы (ячейки от **a5** до **D8**).

6. В диалоговом окне **Выбор источника данных** нажмите кнопку **ОК**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Добавление элементов управления диаграммы во время выполнения в проекте уровня документа
 Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавлять динамически во время выполнения. При закрытии документа динамически созданные диаграммы не сохраняются в документе как элементы управления ведущего приложения. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Добавление элемента управления «Диаграмма» на лист программным образом

1. В обработчике событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> для `Sheet1` вставьте следующий код, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Добавление элементов управления диаграммы во время выполнения в проекте надстройки VSTO
 Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавить программным образом на любой открытый лист в проекте надстройки VSTO. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

 При закрытии листа динамически созданные элементы управления «Диаграмма» не сохраняются в листе как элементы управления ведущего приложения. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Добавление элемента управления «Диаграмма» на лист программным образом

1. Следующий код создает ведущий элемент листа, который основан на открытом листе, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере необходимо соблюдать следующие требования.

- Данные для диаграммы хранятся в диапазоне с A5 по D8 на листе.

## <a name="see-also"></a>См. также раздел
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Элемент управления диаграммы](../vsto/chart-control.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
