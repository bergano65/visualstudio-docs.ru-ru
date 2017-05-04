---
title: "Практическое руководство. Заполнение документов данными из объектов | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], заполнение данными"
  - "данные [разработка решений Office в Visual Studio], добавление в документы"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Практическое руководство. Заполнение документов данными из объектов
  Доступ к данным в объекте данных в проектах уровня документа Microsoft Office Word осуществляется точно так же, как в проектах Windows Forms. Для получения данных из объекта в решении можно использовать те же средства и компоненты кода. Также можно использовать элементы управления Windows Forms для отображения данных. Кроме того, данные можно показать с помощью элементов управления ведущего приложения. Элементы управления ведущего приложения представляют собой управляемые объекты Microsoft Office Word, дополненные событиями и функциями привязки данных. Для получения дополнительной информации см. [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Чтобы заполнить документ данными из объекта, необходимо выполнить три основных действия:  
  
-   добавить в документ элемент управления, который можно привязать к данным;  
  
-   добавить данные из объекта в документ;  
  
-   подключить объект данных к BindingSource.  
  
## Добавление объекта данных  
  
#### Добавление объекта данных  
  
-   Откройте окно **Источники данных** и создайте источник данных из объекта. Для получения дополнительной информации см. [Практическое руководство. Подключение к данным в объектах](http://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).  
  
## Подключение объекта данных к BindingSource  
 В проектах уровня документа вы добавляете элементы управления в документ и привязываете их к данным во время разработки.  
  
 В проектах надстроек VSTO вы создаете элементы управления и привязываете их во время выполнения.  
  
### Проекты уровня документа  
  
##### Подключение объекта данных к BindingSource  
  
1.  Перетащите нужное поле данных из окна **Источники данных** в документ. При этом автоматически создается элемент управления.  
  
2.  Создайте в коде экземпляр типа объекта, выбранного в качестве источника данных.  
  
3.  Присвойте этот экземпляр свойству <xref:System.Windows.Forms.BindingSource.DataSource%2A> объекта <xref:System.Windows.Forms.BindingSource>.  
  
### Проекты уровня приложения  
  
##### Подключение объекта данных к BindingSource  
  
1.  Создайте в коде экземпляр типа объекта, связанного с источником данных.  
  
2.  Создайте экземпляр класса <xref:System.Windows.Forms.BindingSource>.  
  
3.  Присвойте экземпляр источника данных свойству <xref:System.Windows.Forms.BindingSource.DataSource%2A> объекта <xref:System.Windows.Forms.BindingSource>.  
  
4.  Добавьте источник данных как привязку данных к элементу управления.  
  
## См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Общие сведения об источниках данных](../data-tools/add-new-data-sources.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Подключение к данным в приложениях Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Общие сведения о компоненте BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  