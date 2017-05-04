---
title: "Практическое руководство. Заполнение листов данными из базы данных | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "данные [разработка решений Office в Visual Studio], добавление к листам"
  - "базы данных [разработка решений Office в Visual Studio], заполнение листов"
  - "листы [разработка решений Office в Visual Studio], заполнение"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Практическое руководство. Заполнение листов данными из базы данных
  Доступ к данным в проектах office уровня документа так же, как и в проектах Windows Forms.  Для переноса данных в решение могут использоваться те же средства и компоненты кода. Кроме того, можно использовать элементы управления Windows Forms для отображения данных.  Также поддерживается использование элементов управления ведущего приложения, которые представляют собой собственные объекты приложения Microsoft Office Excel, улучшенные функциональными возможностями привязки данных и событий.  Дополнительные сведения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В приведенном ниже примере кода показано добавление элементов управления с привязкой к данным в проекты уровня документа с помощью конструктора.  Пример добавления элементов управления с привязкой к данным в проекты уровня приложения во время выполнения см. в разделе [Пошаговое руководство. Сложная привязка данных в проекте надстройки VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Для просмотра связанных демонстрационных видеороликов перейдите по ссылкам [How Do I: Transfer Data Into an Excel Worksheet?](http://go.microsoft.com/fwlink/?LinkID=130277) и [How Do I: Consume Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## Добавление элемента управления с привязкой к данным на лист во время разработки  
  
#### Заполнение листов данными из базы данных  
  
1.  В конструкторе Visual Studio откройте лист проекта уровня документа для Excel.  
  
2.  Откройте окно **Источники данных** и создайте источник данных для проекта.  Дополнительные сведения см. в разделе [Практическое руководство. Подключение к данным в базе данных](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Перетащите на лист необходимое поле или таблицу из окна **Источники данных**.  
  
 один из следующих элементов управления:  
  
-   При перетаскивании поля на листе создается элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Дополнительные сведения см. в разделе [Элемент управления NamedRange](../vsto/namedrange-control.md).  
  
-   При перетаскивании таблицы на листе создается элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>.  Дополнительные сведения см. в разделе [Элемент управления ListObject](../vsto/listobject-control.md).  
  
 Чтобы добавить другой элемент управления, выберите таблицу или поле в окне **Источники данных**, затем в раскрывающемся списке выберите другой элемент управления .  
  
## Объекты проекта.  
 Кроме элемента управления, в проект автоматически добавляются следующие объекты, связанные с данными:  
  
-   Типизированный набор данных, который инкапсулирует таблицы данных из базы данных, к которым было осуществлено подключение.  Дополнительные сведения см. в разделе [Работа с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Класс <xref:System.Windows.Forms.BindingSource>, который подключает элемент управления к типизированному набору данных.  Дополнительные сведения см. в разделе [Общие сведения о компоненте BindingSource](../Topic/BindingSource%20Component%20Overview.md).  
  
-   Класс TableAdapter, который подключает типизированный набор данных к базе данных.  Дополнительные сведения см. в разделе [Общие сведения об адаптере таблиц](/visual-studio/data-tools/tableadapter-overview).  
  
-   TableAdapterManager, который используется для координации адаптеров таблицы в наборе данных, чтобы включить иерархические обновления.  Дополнительные сведения см. в разделах [Иерархическое обновление](../data-tools/hierarchical-update.md) и [Общие сведения о компоненте TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 При выполнении проекта, элемент управления отображает первую запись в источнике данных.   Можно использовать <xref:System.Windows.Forms.BindingSource>, чтобы дать пользователям возможность прокрутки записей.  
  
#### Прокрутка записей  
  
-   Используйте методы класса <xref:System.Windows.Forms.BindingSource>, такие как <xref:System.Windows.Forms.BindingSource.MoveNext%2A> и <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Дополнительные сведения о том, как отправлять обновления типизированному набору данных и базе данных см. в разделе [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Общие сведения об источниках данных](../data-tools/add-new-data-sources.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Практическое руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Инструкции: Передайте данные в листе Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Инструкции: Данные базы данных потребления в Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  