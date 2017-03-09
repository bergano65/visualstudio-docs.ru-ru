---
title: "Практическое руководство. Создание запросов TableAdapter | Microsoft Docs"
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
  - "данные [Visual Studio], запросы TableAdapter"
  - "запросы [Visual Studio], создание"
  - "запросы [Visual Studio], адаптеры таблиц TableAdapter"
  - "адаптеры таблиц TableAdapter, создание запросов"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Практическое руководство. Создание запросов TableAdapter
Запросы TableAdapter являются инструкциями SQL или сохраненными процедурами, которые приложение может выполнять в базе данных.  
  
 Добавьте в TableAdapter столько запросов, сколько требуется в приложении.  Запросы TableAdapter отображаются в виде методов на TableAdapter.  При создании запроса с именем `FillByCity`, принимающего параметр, представляющий значение города, запрос добавляется в TableAdapter.  Он добавляется в качестве типизированного метода, который принимает корректный тип параметра в качестве аргумента – в данном случае строку, представляющую значение города.  Любой запрос TableAdapter вызывается так же, как любой метод на любом объекте.  Например, следующий код выполняет запрос `FillByCity` и заполняет таблицу `Customers` значениями клиентов со значением города, равным `Seattle`:  
  
 [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
 Запросы TableAdapter могут заполнять таблицы данных \(запросы `Fill` и `FillBy`\) или возвращать новые заполненные таблицы данных по запросам \( запросы `GetData` и `GetDataBy`\).  
  
 Можно добавить запросы для существующих TableAdapter, запустив мастер [мастер настройки запроса TableAdapter](../data-tools/editing-tableadapters.md).  \(Щелкните правой кнопкой мыши TableAdapter и выберите команду **Добавить запрос**.\)  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Создание запроса в Конструкторе наборов данных  
  
#### Для добавления запроса в TableAdapter с помощью Конструктора наборов данных:  
  
1.  Откройте набор данных в **Конструкторе наборов данных**.  Дополнительные сведения см. в разделе [Практическое руководство. Открытие набора данных в конструкторе наборов данных](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Щелкните правой кнопкой мыши нужный TableAdapter и выберите **Добавить запрос**.  
  
     \-или\-  
  
3.  Перетащите **Запрос** из вкладки **Набор данных Панели элементов** в таблицу Конструктора.  
  
     Откроется **Мастер настройки запроса адаптера таблицы**.  
  
4.  Завершите работу мастера; запрос добавляется к адаптеру таблицы.  
  
## Создание запроса непосредственно на форме в приложении Windows  
 Если на форме имеется экземпляр TableAdapter, можно добавить запрос с помощью [Диалоговое окно "Построитель условий поиска"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md), который добавляет элемент управления <xref:System.Windows.Forms.ToolStrip> на форму, принимающую все входные параметры, необходимые запросу, а также содержит кнопку для выполнения запроса.  
  
#### Добавление запроса в TableAdapter с помощью диалогового окна "Критерии поиска"  
  
1.  Выберите TableAdapter в панели компонентов.  
  
2.  Щелкните смарт\-тег TableAdapter и выберите **Добавить запрос**.  
  
3.  Завершите работу диалогового окна, и запрос будет добавлен в TableAdapter.  Дополнительные сведения см. в разделе [Диалоговое окно "Построитель условий поиска"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## См. также  
 [Общие сведения об адаптере таблиц](../data-tools/tableadapter-overview.md)   
 [Практическое руководство. Изменение запросов TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)   
 [Общие сведения об источниках данных](../data-tools/add-new-data-sources.md)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Практическое руководство. Переход между данными с помощью элемента управления BindingNavigator в Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Пошаговое руководство. Отображение данных на форме в приложении Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Пошаговое руководство. Создание адаптера таблицы с несколькими запросами](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)