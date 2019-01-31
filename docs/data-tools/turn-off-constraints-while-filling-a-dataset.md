---
title: Отключение ограничений при заполнении набора данных
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b78bd412343888a5f90fdc84f1c4fe31a3babaa7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996770"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Отключение ограничений при заполнении набора данных

Если набор данных содержит ограничения (например, ограничения внешнего ключа), они могут вызывать ошибки, связанные с порядку операции, выполняемые над набором данных. Например загрузка дочерних записей перед загрузкой связанных родительских записей может вызвать ошибку и нарушают ограничение. Как только вы загружаете дочерней записи, ограничение проверяет связанной родительской записи и вызывает ошибку.

Если нет механизм, позволяющий временное отключение ограничения, возникает ошибка, каждый раз при попытке загрузить запись в дочерней таблице ниже. Другой способ приостановить все ограничения в наборе данных — с помощью <xref:System.Data.DataRow.BeginEdit%2A>, и <xref:System.Data.DataRow.EndEdit%2A> свойства.

> [!NOTE]
> События проверки (например, <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging>) не будет вызываться при отключенных ограничениях.

## <a name="to-suspend-update-constraints-programmatically"></a>Чтобы приостановить обновления ограничения программным способом

-   В следующем примере показано, как временно отключить проверку ограничений в набор данных:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Чтобы приостановить ограничения на обновление с помощью конструктора наборов данных

1.  Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание набора данных в конструкторе наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  В окне **Свойства** присвойте свойству <xref:System.Data.DataSet.EnforceConstraints%2A> значение `false`.

## <a name="see-also"></a>См. также

- [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Отношения в наборах данных](../data-tools/relationships-in-datasets.md)