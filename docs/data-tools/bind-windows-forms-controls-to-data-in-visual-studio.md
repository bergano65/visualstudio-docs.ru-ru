---
title: "Привязка элементов управления Windows Forms к данным в Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "данные [Windows Forms], источники данных"
  - "данные [Windows Forms], отображение"
  - "источники данных, отображение данных"
  - "отображение данных в формах"
  - "отображение данных, Windows Forms"
  - "формы, отображение данных"
  - "Windows Forms, привязка данных"
  - "Windows Forms, отображение данных"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Привязка элементов управления Windows Forms к данным в Visual Studio
Для пользователей приложения данные можно отображать путем привязки данных к Windows Forms.  Чтобы создать эти привязанные к данным элементы управления, можно перетащить элементы из окна **Источники данных** в конструктор Windows Forms среды Visual Studio.  В этом разделе описываются некоторые из наиболее распространенных задач, инструментов и классов, которые можно использовать для создания связанных с данными приложений Windows Forms.  
  
 Общие сведения о методах создания связанных с данными элементов управления в Visual Studio см. в разделе [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  Дополнительные сведения о привязке данных в Windows Forms см. в разделе [Связывание элементов управления Windows Forms с данными](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
## Задачи отображения данных на форме в приложении Windows  
 В следующей таблице приведены общие задачи, относящиеся к отображению данных в форме приложения Windows.  
  
|Задача|Дополнительные сведения|  
|------------|-----------------------------|  
|Создайте элементы управления с привязкой к данным<br /><br /> Привязка существующих элементов управления к данным|[Практическое руководство. Привязка элементов управления Windows Forms к данным](../data-tools/bind-windows-forms-controls-to-data.md)|  
|Создание элементов управления, отображающих связанные данные в иерархическом отношении: когда пользователь выбирает запись данных в одном элементе управления, другой элемент управления отображает связанные данные для выбранной записи|[Практическое руководство. Отображение связанных данные в приложении Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)|  
|Создание *таблицы подстановки*.  Таблица подстановки содержит сведения из одной таблицы на основе значения поля внешнего ключа другой таблицы.|[Практическое руководство. Создание таблиц подстановки в приложениях Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|Задание способа управления отображаемыми данными|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/ru-ru/42638120-9e6f-436b-985f-4036664230fd)|  
|Изменение поведения функции интеллектуального захвата в окне **Источники данных**|[Практическое руководство. Настройка способа создания подписи для элемента управления с привязкой к данным в Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|Добавление элементов управления, выполняющих параметризованный запрос|[Практическое руководство. Добавление параметризованного запроса в приложение Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|Указание столбца для использования в качестве элемента управления изображениями в базе данных|[Практическое руководство. Привязка элементов управления к рисункам из базы данных](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|Фильтрация и сортировка данных в наборе данных|[Практическое руководство. Фильтрация и сортировка данных в приложении Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 В следующих разделах предоставлены примеры привязки элементов управления Windows Forms к данным.  
  
 [Пошаговое руководство. Отображение данных на форме в приложении Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 Пошаговые инструкции по запросу данных из базы данных и отображению данных в форме Windows Forms.  
  
 [Пошаговое руководство. Отображение связанных данных на форме в приложении Windows](../Topic/Walkthrough:%20Displaying%20Related%20Data%20on%20a%20Windows%20Form.md)  
 Пошаговые инструкции по отображению данных из двух связанных таблиц и отображению данных в форме Windows Forms.  
  
 [Практическое руководство. Создание формы Windows Forms для поиска данных](../data-tools/create-a-windows-form-to-search-data.md)  
 Пошаговые инструкции по способам создания форм Windows Forms для поиска в базе данных на основе значений, введенных пользователем.  
  
 [Пошаговое руководство. Создание таблицы подстановок в приложении Windows Forms](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 Пошаговые инструкции по способам отображения данных из одной таблицы, основанных на данных, выбранных в другой таблице.  
  
 [Пошаговое руководство. Передача данных между формами Windows Forms](../data-tools/pass-data-between-forms.md)  
 Пошаговые инструкции по передаче значений из одной формы в другую форму приложения.  
  
 [Пошаговое руководство. Создание пользовательского элемента управления Windows Forms с простой привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 Пошаговые сведения о создании пользовательского элемента управления, который можно использовать в окне **Источники данных**.  
  
 [Пошаговое руководство. Создание пользовательского элемента управления Windows Forms со сложной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 Пошаговые сведения о создании пользовательского элемента управления, который можно использовать в окне **Источники данных**.  
  
 [Пошаговое руководство. Создание пользовательского элемента управления Windows Forms с подстановочной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 Пошаговые сведения о создании пользовательского элемента управления, который можно использовать в окне **Источники данных**.  
  
## Cмарт\-теги данных  
 Смарт\-теги, относящиеся к работе с данными, доступны для большого числа элементов управления.  Когда определенные элементы управления добавляются в форму, набор возможных действий, относящихся к данным, доступен через смарт\-теги.  
  
## Компонент BindingSource  
 Компонент <xref:System.Windows.Forms.BindingSource> используется для двух задач.  Во\-первых, он обеспечивает уровень абстракции при выполнении привязки к данным элементов управления в форме.  Элементы управления на форме привязаны к компоненту <xref:System.Windows.Forms.BindingSource> \(в отличие от непосредственной привязки к источнику данных\).  
  
 Во\-вторых, он может управлять коллекцией объектов.  Добавление типа для <xref:System.Windows.Forms.BindingSource> создает список этого типа.  
  
 Дополнительные сведения о компоненте <xref:System.Windows.Forms.BindingSource> см. в следующих разделах.  
  
-   [Компонент BindingSource](../Topic/BindingSource%20Component.md)  
  
-   [Общие сведения о компоненте BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [Архитектура компонента BindingSource](../Topic/BindingSource%20Component%20Architecture.md)  
  
## Элемент управления BindingNavigator  
 Данный компонент предоставляет пользовательский интерфейс для перемещения по данным, отображаемым Windows\-приложением.  Для получения дополнительной информации см. [Элемент управления BindingNavigator](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md).  
  
## Элемент управления DataGridView  
 Элемент управления <xref:System.Windows.Forms.DataGridView> позволяет отображать и редактировать табличные данные из различных типов источников данных.  Можно привязать данные к объекту <xref:System.Windows.Forms.DataGridView> с помощью свойства <xref:System.Windows.Forms.DataGridView.DataSource%2A>.  Для получения дополнительной информации см. [Общие сведения об элементе управления DataGridView](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md).  
  
## См. также  
 [Пошаговые руководства работы с данными](../Topic/Data%20Walkthroughs.md)   
 [окно "Источники данных"](../Topic/Data%20Sources%20Window.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Пошаговое руководство. Отображение данных на форме в приложении Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)   
 [Общие сведения об источниках данных](../data-tools/add-new-data-sources.md)   
 [Пошаговое руководство. Создание пользовательского элемента управления Windows Forms с простой привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Пошаговое руководство. Создание пользовательского элемента управления Windows Forms со сложной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Пошаговое руководство. Создание пользовательского элемента управления Windows Forms с подстановочной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)