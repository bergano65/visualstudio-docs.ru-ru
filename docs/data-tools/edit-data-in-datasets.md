---
title: "Редактирование данных в наборах данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "данные [Visual Studio], правка в наборах данных"
  - "наборы данных [Visual Basic], редактирование данных"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Редактирование данных в наборах данных
Изменение данных в <xref:System.Data.DataSet> представляет собой процесс управления фактическими данными в отдельных объектах <xref:System.Data.DataTable>, которые составляют набор данных.  Изменение данных в таблицах данных подобно изменению данных в таблице любой базы данных — процесс может включать вставку, обновление и удаление записей таблицы.  
  
 Кроме изменения фактических данных, также можно запрашивать <xref:System.Data.DataTable> для возвращения определенных строк данных, например, отдельных строк, определенных версий строк \(исходные и предложенные\), только измененных строк и строк, которые содержат ошибки.  
  
## Общие задачи таблицы данных  
 В следующей таблице приведены ссылки на типовые задачи, связанные с редактированием и запросом данных в наборе данных:  
  
|Задача|Описание|  
|------------|--------------|  
|Вставка новых записей в таблицу данных.|Создание новой <xref:System.Data.DataRow> и добавление ее в коллекцию строк таблицы.  Для получения дополнительной информации см. [Практическое руководство. Добавление строк в объект DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).|  
|Обновление существующих записей в таблице данных.|Присвоение значения конкретному столбцу строки данных.  Для получения дополнительной информации см. [Практическое руководство. Редактирование строк в объекте DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).|  
|Удаление существующих записей из таблицы данных.|Вызов метода <xref:System.Data.DataRow.Delete%2A> для строки, которую требуется удалить из таблицы данных.  Для получения дополнительной информации см. [Практическое руководство. Удаление строк из объекта DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).|  
|Поиск измененных записей в таблице данных.|Вызов метода <xref:System.Data.DataTable.GetChanges%2A> таблицы данных.  Для получения дополнительной информации см. [Практическое руководство. Получение измененных строк](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).|  
|Доступ к различных версиям строки в таблице данных.|Доступ к отдельным столбцам строки данных с помощью передачи <xref:System.Data.DataRowVersion>, которую необходимо просмотреть.  Для получения дополнительной информации см. [Практическое руководство. Получение определенных версий объекта DataRow](../Topic/How%20to:%20Get%20Specific%20Versions%20of%20a%20DataRow.md).|  
|Поиск строк с ошибками в таблице данных.|Проверка свойства <xref:System.Data.DataTable.HasErrors%2A> таблицы данных.  Для получения дополнительной информации см. [Практическое руководство. Поиск строк с ошибками](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).|  
  
## См. также  
 [DataTables](../Topic/DataTables.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [DataTables](../Topic/DataTables.md)   
 [Пошаговые руководства работы с данными](../Topic/Data%20Walkthroughs.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Общие сведения о приложениях для работы с данными в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)