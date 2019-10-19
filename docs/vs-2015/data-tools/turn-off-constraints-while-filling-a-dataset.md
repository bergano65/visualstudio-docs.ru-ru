---
title: Отключение ограничений при заполнении набора данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667168"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Отключение ограничений при заполнении набора данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если набор данных содержит ограничения (например, ограничения внешнего ключа), Сэйкан вызовет ошибки, связанные с порядком операций, выполняемых с набором данных. Например, загрузка дочерних записей перед лоадингрелатед родительскими записями может привести к нарушению ограничения и вызвать ошибку. После загрузки дочерней записи ограничение проверяет связанную родительскую запись и вызывает ошибку.

 Если механизм, позволяющий временно приостановку ограничения, не существовал, при каждой попытке загрузить запись в дочернюю таблицу возникнет ошибка. Еще один способ приостановить все ограничения в наборе данных — с помощью <xref:System.Data.DataRow.BeginEdit%2A> и <xref:System.Data.DataRow.EndEdit%2A> свойств.

> [!NOTE]
> События проверки (например, <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging>) не будут вызываться при отключенных ограничениях.

### <a name="to-suspend-update-constraints-programmatically"></a>Чтобы приостановить ограничения обновления программным способом

- В следующем примере показано, как временно отключить проверку ограничений в наборе данных.

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Приостановка ограничений обновления с помощью конструктор наборов данных

1. Откройте набор данных в конструктор наборов данных. Дополнительные сведения см. в разделе [как открыть набор данных в конструктор наборов данных](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. В окне **Свойства** присвойте свойству <xref:System.Data.DataSet.EnforceConstraints%2A> значение `false`.

## <a name="see-also"></a>См. также раздел
 [Заполнение наборов данных с помощью связей TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md) [в наборах данных](../data-tools/relationships-in-datasets.md)
