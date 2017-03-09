---
title: "Разрешение вопросов, связанных с исключениями: System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NoNullAllowedException - класс"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Data.NoNullAllowedException
Исключение <xref:System.Data.NoNullAllowedException> возникает при попытке вставки значения NULL в столбец, для которого свойство <xref:System.Data.DataColumn.AllowDBNull%2A> установлено в `false`.  
  
## Полезные советы  
 **Проверка на равенство значения DBNull перед добавлением его в столбец.**  
 Если свойство <xref:System.Data.DataColumn.AllowDBNull%2A> установлено в `false`, нельзя вставить пустое значение. Дополнительные сведения см. в разделе <xref:System.DBNull>.  
  
 **Задать для AllowDBNull значение True.**  
 Установка этого свойства в `true` позволит вставлять значения NULL. Для получения дополнительной информации см. <xref:System.Data.DataColumn.AllowDBNull%2A>.  
  
## Примечания  
 Если использовать кнопки переходов для перемещения по записям таблицы базы данных на форме данных, это исключение может быть снабжено дополнительной информацией, "Столбец "столбец" не допускает значения NULL". Причина ошибки в том, что первичный ключ или "не NULL"\-столбец таблицы базы данных не был выбран в мастере форм данных. Если первичный ключ или "не NULL"\-столбец базы данных не выбран в мастере форм данных при создании формы данных, то включен параметр **Добавить — создает новую запись**. Чтобы обойти эту проблему, выберите следующие столбцы из выбранной таблицы при добавлении формы с помощью мастера форм данных: столбец первичного ключа и столбец, который не допускает значения NULL.  
  
## См. также  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)