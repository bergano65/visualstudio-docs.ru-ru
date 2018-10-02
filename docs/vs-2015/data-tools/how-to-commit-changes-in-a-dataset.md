---
title: 'Практическое: зафиксировать изменения в наборе данных | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 40acd2a706ef7bc00ea1f90e51e90705be5658c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568258"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Практическое руководство. Фиксация изменений в наборе данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После внесения изменений в записи в наборе данных, обновления, вставки и удаления записей, набор данных сохраняет исходные и текущие версии записей. Кроме того, каждая строка в <xref:System.Data.DataRow.RowState%2A> свойство следит за ли записи в исходном состоянии или были обновлены, вставлены или удалены. Эта информация полезна в тех случаях, когда необходимо найти определенную версию строки. Как правило получится подмножество всех измененных записей для отправки другому процессу. Дополнительные сведения см. в разделе [как: получение строк изменен](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). После обработки всех измененных строк, можно зафиксировать изменения, вызвав `AcceptChanges` метод <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, или <xref:System.Data.DataRow>. `AcceptChanges` Метод автоматически вызывается при вызове методов обновления [TableAdapter](../data-tools/tableadapter-overview.md) или адаптер данных. Вызовите `AcceptChanges` после отправки изменений в базу данных.  
  
 При вызове <xref:System.Data.DataSet.AcceptChanges%2A> на <xref:System.Data.DataSet>любые <xref:System.Data.DataRow> объектов, находящихся в режиме успешно завершить свои изменения. <xref:System.Data.DataRow.RowState%2A> Свойства каждого <xref:System.Data.DataRow> также изменяется; <xref:System.Data.DataRowState> и <xref:System.Data.DataRowState> строк становятся <xref:System.Data.DataRowState>, и <xref:System.Data.DataRowState> строки будут удалены.  
  
 Если <xref:System.Data.DataSet> содержит <xref:System.Data.ForeignKeyConstraint> объектов, вызов <xref:System.Data.DataSet.AcceptChanges%2A> метод также вызывает <xref:System.Data.AcceptRejectRule> для применения.  
  
### <a name="to-commit-changes-in-a-dataset"></a>Чтобы внести изменения в набор данных  
  
-   Вызовите `AcceptChanges` метод <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, или <xref:System.Data.DataRow> для фиксации изменений в этих объектах.  
  
     В следующем примере показан вызов `AcceptChanges` для фиксирования изменений в `Customers` после обновления источника данных:  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Практическое: получение измененных строк](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)