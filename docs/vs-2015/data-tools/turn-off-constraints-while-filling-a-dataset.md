---
title: Отключение ограничений при заполнении набора данных | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c47d3cb5e02117cb75ab86579b0cb3b166bd510
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259913"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Отключение ограничений при заполнении набора данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Если набор данных содержит ограничения (например, ограничения внешнего ключа), theycan вызывать ошибки, связанные с порядку операции, выполняемые над набором данных. Например загрузка дочерних записей перед loadingrelated родительские записи можно нарушают ограничение и привести к ошибке. Как только вы загружаете дочерней записи, ограничение проверяет связанной родительской записи и вызывает ошибку.  
  
 Если нет механизм, позволяющий временное отключение ограничения, возникает ошибка, каждый раз при попытке загрузить запись в дочерней таблице ниже. Другой способ приостановить все ограничения в наборе данных — с помощью <xref:System.Data.DataRow.BeginEdit%2A>, и <xref:System.Data.DataRow.EndEdit%2A> свойства.  
  
> [!NOTE]
>  События проверки (например, <xref:System.Data.DataTable.ColumnChanging> и<xref:System.Data.DataTable.RowChanging>) не будет вызываться при отключенных ограничениях.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Чтобы приостановить обновления ограничения программным способом  
  
-   В следующем примере показано, как временно отключить проверку ограничений в набор данных:  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Чтобы приостановить ограничения на обновление с помощью конструктора наборов данных  
  
1.  Откройте набор данных в [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md). Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  В окне **Свойства** присвойте свойству <xref:System.Data.DataSet.EnforceConstraints%2A> значение `false`.  
  
## <a name="see-also"></a>См. также  
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Отношения в наборах данных](../data-tools/relationships-in-datasets.md)

