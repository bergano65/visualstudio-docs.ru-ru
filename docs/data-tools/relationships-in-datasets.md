---
title: "Отношения в наборах данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "наборы данных [Visual Basic], связи"
  - "связи, сведения об отношениях"
  - "связи, наборы данных"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Отношения в наборах данных
Набор данных может содержать связанные таблицы, как реляционная база данных.  **DataRelation** – это объект, упрощающий связь между таблицами данных.  В следующих разделах содержатся сведения об объектах ADO.NET **DataRelation**, о процедуре их создания и об их использовании для работы с данными в связанных таблицах.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## В этом подразделе  
 [Знакомство с объектами DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 Предоставляет общие сведения о том, как наборы данных позволяют указывать отношения между таблицами и как можно эффективно использовать эти отношения.  
  
 [Практическое руководство. Создание объектов DataRelation с помощью конструктора набора данных](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 Объясняет, как использовать **конструктор наборов данных** для добавления объекта <xref:System.Data.DataRelation> в набор данных.  
  
 [Практическое руководство. Получение доступа к записям в связанных объектах DataTable](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 Объясняет, как программно вернуть связанные записи в типизированном наборе данных с таблицами в отношении "один ко многим".  
  
 [Пошаговое руководство. Создание отношений между таблицами данных](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 Предоставляет пошаговые инструкции по созданию двух таблиц данных с помощью **Конструктора наборов данных** и добавлению отношения между ними.  
  
## Ссылка  
 <xref:System.Data.DataRelation>  
 Представляет отношение родительский\/дочерний между двумя объектами T:System.Data.DataTable.  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 Принимает дочерние строки T:System.Data.DataRow.  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 Принимает родительские строки T:System.Data.DataRow.  
  
 <xref:System.Data.Rule>  
 Указывает действие, которое должно быть выполнено для обеспечения ограничения <xref:System.Data.ForeignKeyConstraint>.  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 Получает или задает значение, показывающее, должны ли значения в каждой строке столбца быть уникальными.  
  
 <xref:System.Data.Constraint>  
 Представляет ограничение, которое может быть применено к одному или более объектам <xref:System.Data.DataColumn>.  
  
## Связанные подразделы  
 [Добавление объектов DataRelation](../Topic/Adding%20DataRelations.md)  
 Описывает создание отношений между таблицами, входящими в объект <xref:System.Data.DataSet>.  
  
 [Перемещение по связям DataRelations](../Topic/Navigating%20DataRelations.md)  
 Описывает использование отношений между таблицами объекта <xref:System.Data.DataSet> для возвращения дочерних или родительских строк.  
  
 [Вложенность объектов DataRelation](../Topic/Nesting%20DataRelations.md)  
 Рассматривает важность вложенных объектов <xref:System.Data.DataRelation> при представлении содержимого <xref:System.Data.DataSet> в виде данных XML и описывает способы их создания.