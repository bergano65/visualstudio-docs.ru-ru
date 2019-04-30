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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e75f06a999638f1346b1304fd438a8cc3f6b0b6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424983"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Отключение ограничений при заполнении набора данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если набор данных содержит ограничения (например, ограничения внешнего ключа), theycan вызывать ошибки, связанные с порядку операции, выполняемые над набором данных. Например загрузка дочерних записей перед loadingrelated родительские записи можно нарушают ограничение и привести к ошибке. Как только вы загружаете дочерней записи, ограничение проверяет связанной родительской записи и вызывает ошибку.  
  
 Если нет механизм, позволяющий временное отключение ограничения, возникает ошибка, каждый раз при попытке загрузить запись в дочерней таблице ниже. Другой способ приостановить все ограничения в наборе данных — с помощью <xref:System.Data.DataRow.BeginEdit%2A>, и <xref:System.Data.DataRow.EndEdit%2A> свойства.  
  
> [!NOTE]
> События проверки (например, <xref:System.Data.DataTable.ColumnChanging> и<xref:System.Data.DataTable.RowChanging>) не будет вызываться при отключенных ограничениях.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Чтобы приостановить обновления ограничения программным способом  
  
- В следующем примере показано, как временно отключить проверку ограничений в набор данных:  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Чтобы приостановить ограничения на обновление с помощью конструктора наборов данных  
  
1. Откройте набор данных в конструкторе наборов данных. Дополнительные сведения см. в разделе [Как Откройте набор данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. В окне **Свойства** присвойте свойству <xref:System.Data.DataSet.EnforceConstraints%2A> значение `false`.  
  
## <a name="see-also"></a>См. также  
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Отношения в наборах данных](../data-tools/relationships-in-datasets.md)
