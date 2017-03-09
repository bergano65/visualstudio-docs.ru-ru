---
title: "Практическое руководство. Фиксация изменений в наборе данных | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "наборы данных [Visual Basic], сохранение изменений"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Практическое руководство. Фиксация изменений в наборе данных
При внесении изменений в записи набора данных с помощью обновления, вставки и удаления записей набор данных сохраняет исходную и текущую версии записей.  Кроме того, свойство <xref:System.Data.DataRow.RowState%2A> каждой строки следит за тем, находится ли запись в исходном состоянии или была обновлены, вставлена или удалена.  Эти сведения можно использовать, когда требуется найти определенную версию строки.  Обычно пери этом поступает подмножество всех измененных записей для отправки другому процессу.  Дополнительные сведения см. в разделе [Практическое руководство. Получение измененных строк](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  После обработки всех измененных строк можно внести изменения посредством вызова метода `AcceptChanges`, принадлежащего <xref:System.Data.DataSet>, <xref:System.Data.DataTable> или <xref:System.Data.DataRow>.  Метод `AcceptChanges` вызывается автоматически при вызове методов обновления [TableAdapter](../data-tools/tableadapter-overview.md) или адаптера данных.  Метод `AcceptChanges` вызывается после подтверждения изменений в базе данных.  
  
 При вызове метода <xref:System.Data.DataSet.AcceptChanges%2A> для класса <xref:System.Data.DataSet> завершается изменение любых объектов <xref:System.Data.DataRow>, находящихся в режиме изменения.  Свойство <xref:System.Data.DataRow.RowState%2A> каждого <xref:System.Data.DataRow> также изменяется; строки <xref:System.Data.DataRowState> и <xref:System.Data.DataRowState> становятся <xref:System.Data.DataRowState>, и строки <xref:System.Data.DataRowState> удаляются.  
  
 Если класс <xref:System.Data.DataSet> содержит объекты <xref:System.Data.ForeignKeyConstraint>, то при вызове метода <xref:System.Data.DataSet.AcceptChanges%2A> будет выполняться свойство <xref:System.Data.AcceptRejectRule>.  
  
### Чтобы внести изменения в набор данных  
  
-   Вызовите метод `AcceptChanges` в <xref:System.Data.DataSet>, <xref:System.Data.DataTable> или <xref:System.Data.DataRow>, чтобы внести изменения в этих объектах.  
  
     В следующем примере показано, как вызвать метод `AcceptChanges`, чтобы внести изменения в таблице `Customers` после обновления источника данных:  
  
     [!CODE [VbRaddataEditing#11](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#11)]  
  
## См. также  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Практическое руководство. Получение измененных строк](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)