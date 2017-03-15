---
title: "Практическое руководство. Расширение функциональных возможностей адаптера таблицы | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "данные [Visual Studio], расширение TableAdapters"
  - "данные [Visual Studio], адаптеры таблиц TableAdapter"
  - "адаптеры таблиц TableAdapter, добавление функциональных возможностей"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Расширение функциональных возможностей адаптера таблицы
Функциональные возможности адаптера таблиц можно расширить путем добавления кода в файл разделяемого класса адаптера таблицы.  
  
 Код, определяющий адаптер таблицы, генерируется повторно при внесении любых изменений в адаптер таблицы \(в **Конструкторе наборов данных** \) или во время выполнения мастеров, изменяющих конфигурацию адаптера таблицы.  Чтобы избежать удаления кода при повторной генерации адаптера таблицы, добавьте код в файл разделяемого класса адаптера таблицы.  
  
 \(Разделяемые классы позволяют коду определенного класса разделяться между несколькими физическими файлами.  Дополнительные сведения см. в разделе [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) или [partial \(тип\)](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
## Поиск адаптеров таблиц в коде  
 Если адаптеры таблиц создаются с помощью **Конструктора наборов данных**, созданные классы адаптеров таблиц не создаются как вложенные классы <xref:System.Data.DataSet>.  Адаптеры таблиц находятся в пространстве имен, основанном на имени набора данных, связанного с адаптером таблицы.  Например, если приложение содержит набор данных с именем `HRDataSet`, адаптеры таблиц должны быть расположены в пространстве имен `HRDataSetTableAdapters`.  \(Именование соответствует следующему шаблону: *ИмяНабораДанных* \+ `TableAdapters`\).  
  
 В следующем примере предполагается наличие адаптера таблицы с именем `CustomersTableAdapter` в проекте с `NorthwindDataSet`.  
  
#### Для создания разделяемого класса адаптера таблиц  
  
1.  Добавьте новый класс в проект, выбрав команду **Добавить класс** в меню **Проект**.  
  
2.  Назовите класс `CustomersTableAdapterExtended`.  
  
3.  Нажмите кнопку **Добавить**.  
  
4.  Замените код правильным пространством имен и именем разделяемого класса для проекта.  Примеры.  
  
     [!CODE [VbRaddataTableAdapters#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#2)]  
  
## См. также  
 [Общие сведения об адаптере таблиц](../data-tools/tableadapter-overview.md)   
 [Практическое руководство. Создание адаптера таблицы](../data-tools/create-and-configure-tableadapters.md)   
 [Практическое руководство. Создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Практическое руководство. Расширение функциональных возможностей набора данных](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
 [Пошаговые руководства работы с данными](../Topic/Data%20Walkthroughs.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Общие сведения о приложениях для работы с данными в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)