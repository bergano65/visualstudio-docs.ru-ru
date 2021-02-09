---
title: Как программно добавлять строки и столбцы в таблицы Word
description: Узнайте, как можно использовать метод Add объекта Rows для добавления строк в таблицу. Для добавления столбцов также можно использовать метод Add объекта Columns.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a4077e78da512ef7b49546ae9b5271b5dfd8ff15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910170"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Как программно добавлять строки и столбцы в таблицы Word
  В таблице Microsoft Office Word ячейки организованы по строкам и столбцам. Вы можете использовать метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> объекта <xref:Microsoft.Office.Interop.Word.Rows> для добавления строк в таблицу и метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> объекта <xref:Microsoft.Office.Interop.Word.Columns> для добавления столбцов.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Примеры настройки на уровне документа
 Следующие примеры кода можно использовать в настройке на уровне документа. Чтобы использовать эти примеры, выполняйте их из класса `ThisDocument` в своем проекте. В этих примерах предполагается, что документ, связанный с настройкой, уже содержит по крайней мере одну таблицу.

> [!IMPORTANT]
> Этот код выполняется только в тех проектах, которые создаются с помощью любого из следующих шаблонов проекта:
>
> - Документ Word 2013
> - Шаблон Word 2013
> - Документ Word 2010
> - Шаблон Word 2010
>
>   Если вы хотите выполнить эту задачу в любом другом типе проекта, необходимо добавить ссылку на сборку **Microsoft. Office. Interop. Word** , а затем использовать классы из этой сборки для добавления строк и столбцов в таблицы. Дополнительные сведения см. [в разделе руководство. Назначение приложений Office через основные сборки взаимодействия](how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Добавление строки в таблицу

1. Используйте метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>, чтобы добавить строку в таблицу.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Добавление столбца в таблицу

1. Используйте метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, а затем метод <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>, чтобы сделать все столбцы одинаковой ширины.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>Примеры надстроек VSTO
 Следующие примеры кода можно использовать в надстройке VSTO. Чтобы использовать эти примеры, выполняйте их из класса `ThisAddIn` в своем проекте. В этих примерах предполагается, что активный документ содержит хотя бы одну таблицу.

> [!IMPORTANT]
> Этот код выполняется только в тех проектах, которые создаются с помощью шаблонов Word VSTO.
>
> Если вы хотите выполнить эту задачу в любом другом типе проекта, необходимо добавить ссылку на сборку **Microsoft. Office. Interop. Word** , а затем использовать классы из этой сборки для добавления строк и столбцов в таблицы. Дополнительные сведения см. [в разделе руководство. Назначение приложений Office через основные сборки взаимодействия](how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Добавление строки в таблицу

1. Используйте метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>, чтобы добавить строку в таблицу.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Добавление столбца в таблицу

1. Используйте метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, а затем метод <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>, чтобы сделать все столбцы одинаковой ширины.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное создание таблиц Word](how-to-programmatically-create-word-tables.md)
- [Руководство. Программное добавление текста и форматирования в ячейки в таблицах Word](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Руководство. Программное заполнение таблиц Word свойствами документа](how-to-programmatically-populate-word-tables-with-document-properties.md)
