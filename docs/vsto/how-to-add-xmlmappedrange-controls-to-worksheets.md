---
title: Как добавить элементы управления XMLMappedRange на листы
description: Сведения о том, что при сопоставлении элемента XML с ячейкой в Microsoft Office Excel Visual Studio автоматически добавляет на лист элемент управления XmlMappedRange.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 065a904047630d15a8e9ed167a6a4a2764858387
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970326"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Как добавить элементы управления XMLMappedRange на листы
  При сопоставлении элемента XML с ячейкой в Microsoft Office Excel Visual Studio автоматически добавляет <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> на лист элемент управления.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Элемент управления недоступен на **панели элементов** или в окне **Источники данных** . Кроме того, нельзя создавать <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элементы управления программным способом.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Добавление элемента управления XMLMappedRange на лист

1. Откройте книгу Excel в конструкторе Visual Studio.

2. Откройте лист, в который нужно добавить элемент управления.

3. На вкладке **разработчик** щелкните **источник**.

    > [!NOTE]
    > Если вкладка **разработчик** не отображается на ленте, ее необходимо включить. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Откроется область задач **Источник XML** .

4. В области задач **Источник XML** щелкните элемент **карты XML**.

5. В диалоговом окне **карты XML** нажмите кнопку **Добавить**.

     Откроется диалоговое окно **Источник XML** .

6. Выберите XML-схему из диалогового окна **Источник XML** и нажмите кнопку **Открыть**.

     Схема добавляется в диалоговое окно **карты XML** .

7. В диалоговом окне **карты XML** нажмите кнопку **ОК**.

8. Перетащите элемент из области задач **Источник XML** в ячейку листа.

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Создается и добавляется в проект.

    > [!NOTE]
    > При перетаскивании родительского элемента из области задач **Источник XML** <xref:Microsoft.Office.Tools.Excel.ListObject> создается элемент управления.

## <a name="see-also"></a>См. также раздел
- [Элемент управления XmlMappedRange](../vsto/xmlmappedrange-control.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Как сопоставлять схемы с листами в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
