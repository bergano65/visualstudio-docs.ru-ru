---
title: "Отключения ограничений при заполнении набора данных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 29b24794c74f2bd042845384d72a3716506d5e2d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Отключения ограничений при заполнении набора данных
Если набор данных содержит ограничения (например, ограничения foreign key), они могут вызывать ошибки, связанные с порядком операций, выполняемых над набором данных. Например загрузка дочерних записей перед загрузкой связанных родительских записей может вызвать ошибку и нарушают ограничение. Сразу после загрузки дочерней записи ограничение проверяет связанной родительской записи и вызывает ошибку.  
  
 При отсутствии механизма, позволяющего приостанавливать работу ограничений, каждый раз при попытке загрузить запись в дочерней таблице, будет выдана ошибка. Другой способ приостановить все ограничения в наборе данных — с <xref:System.Data.DataRow.BeginEdit%2A>, и <xref:System.Data.DataRow.EndEdit%2A> свойства.  
  
> [!NOTE]
>  События проверки (например, <xref:System.Data.DataTable.ColumnChanging> и<xref:System.Data.DataTable.RowChanging>) не будет вызываться при отключенных ограничениях.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Чтобы приостановить ограничения на обновление программным способом  
  
-   В следующем примере показано, как временно отключить проверку ограничений в наборе данных:  
  
     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Чтобы приостановить ограничения на обновление с помощью конструктора наборов данных  
  
1.  Откройте свой набор данных в **конструктора наборов данных**. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание набора данных в конструкторе наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  В **свойства** задайте <xref:System.Data.DataSet.EnforceConstraints%2A> свойства `false`.  
  
## <a name="see-also"></a>См. также  
 [Заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Отношения в наборах данных](../data-tools/relationships-in-datasets.md)