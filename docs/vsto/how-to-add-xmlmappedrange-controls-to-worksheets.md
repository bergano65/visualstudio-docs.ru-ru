---
title: Практическое руководство. Добавление элементов управления XMLMappedRange на листы
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60f1fe8330e3a40676738c4187273ee60215db6d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427434"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Практическое руководство. Добавление элементов управления XMLMappedRange на листы
  При сопоставлении XML-элемент с ячейкой в Microsoft Office Excel, Visual Studio автоматически добавляет <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> лист элемента управления.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Элемент управления не доступен на **элементов** или **источников данных** окна. Кроме того, нельзя создать <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управляет программным способом.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Чтобы добавить элемент управления XMLMappedRange на лист

1. Откройте книгу Excel в конструкторе Visual Studio.

2. Откройте лист, где вы хотите добавить элемент управления.

3. На **разработчика** щелкните **источника**.

    > [!NOTE]
    > Если **разработчика** вкладка не отображается на ленте, необходимо включить ее. Дополнительные сведения см. в разделе [Как Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     **Источник XML** отображается область задач.

4. В **источник XML** области задач, щелкните **карт XML**.

5. В **карт XML** диалоговом окне щелкните **добавить**.

     **Источник XML** откроется диалоговое окно.

6. Выберите схему XML из **источник XML** диалоговое окно и нажмите кнопку **откройте**.

     Схема добавляется в **карт XML** диалоговое окно.

7. В **карт XML** диалоговом окне щелкните **ОК**.

8. Перетащите элемент из **источник XML** область задач в ячейку на листе.

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Создается и добавляется в проект.

    > [!NOTE]
    > При перетаскивании родительского элемента из **источник XML** область задач <xref:Microsoft.Office.Tools.Excel.ListObject> создается элемент управления.

## <a name="see-also"></a>См. также
- [Элемент управления XmlMappedRange](../vsto/xmlmappedrange-control.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
