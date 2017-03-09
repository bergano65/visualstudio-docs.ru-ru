---
title: "Привязка элементов управления WPF к данным в Visual Studio | Microsoft Docs"
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
  - "данные [WPF], отображение"
  - "привязка данных, WPF"
  - "отображение данных, WPF"
  - "WPF [WPF], данные"
  - "привязка данных WPF [Visual Studio]"
  - "конструктор WPF, привязка данных"
  - "WPF, привязка данных в Visual Studio"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Привязка элементов управления WPF к данным в Visual Studio
Для пользователей приложения данные можно отображать путем привязки данных к элементам управления [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)].  Для создания таких связанных с данными элементов управления можно перетаскивать элементы из окна **Источники данных** на [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  В этом разделе описываются некоторые из наиболее распространенных задач, инструментов и классов, которые можно использовать для создания связанных с данными приложений [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)].  
  
 Общие сведения о создании связанных с данными элементов управления в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] см. в разделе [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Дополнительные сведения о привязке данных [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] см. в разделе [Общие сведения о связывании данных](../Topic/Data%20Binding%20Overview.md).  
  
## Задачи, решаемые в процессе привязки элементов управления WPF к данным  
 В следующей таблице перечислены задачи, которые могут быть решены путем перетаскивания элементов из окна **Источники данных** в [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Задача|Дополнительные сведения|  
|------------|-----------------------------|  
|Создание новых элементов управления, связанных с данными<br /><br /> Привязка существующих элементов управления к данным|[Практическое руководство. Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|Создание элементов управления, отображающих связанные данные в иерархическом отношении: когда пользователь выбирает родительскую запись данных в одном элементе управления, другой элемент управления отображает связанные дочерние данные для выбранной записи|[Практическое руководство. Отображение связанных данных в приложениях WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Создание *таблицы подстановки*, которая отображает информацию из одной таблицы на основе значения в поле внешнего ключа в другой таблице|[Практическое руководство. Создание таблиц подстановки в приложениях WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Привязка элемента управления к изображению в базе данных|[Практическое руководство. Привязка элементов управления к рисункам из базы данных](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## Допустимые целевые объекты перетаскивания  
 Элементы в окне **Источники данных** можно перетаскивать только на допустимые целевые объекты перетаскивания в [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  Имеется две основных разновидности допустимых целевых объектов перетаскивания: контейнеры и элементы управления.  Контейнер — это элемент пользовательского интерфейса, который обычно содержит элементы управления.  Например, сетка является контейнером, равно как и окно.  
  
## Созданный язык XAML и код  
 При перетаскивании элемента из окна **Источники данных** в [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который определяет новый связанный с данными элемент управления \(либо создает привязку существующего элемента управления к источнику данных\).  Для некоторых источников данных [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] также создает код в файле кода программной части, который наполняет данными источник данных.  
  
 В следующей таблице отображены [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] и код, создаваемые [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для каждого типа источников данных в окне **Источники данных**.  
  
|Источник данных|Создание языка XAML, который привязывает элемент управления к источнику данных|Создание кода, который заполняет данными источник данных|  
|---------------------|------------------------------------------------------------------------------------|--------------------------------------------------------------|  
|Набор данных|Да|Да|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Да|Да|  
|Служба|Да|Нет|  
|Объект|Да|Нет|  
  
### Наборы данных  
 При перетаскивании таблицы или столбца из окна **Источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который выполняет следующие действия.  
  
-   Добавление набора данных и нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент.  <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в наборе данных.  
  
-   Создание привязки данных для элемента управления.  Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу.  Если перетащить элемент на контейнер, язык XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к этому элементу.  Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
 Кроме того, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] вносит следующие изменения в файл кода программной части:  
  
-   Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)], который содержит элемент управления.  Обработчик событий наполняет таблицу данными, извлекает <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом.  Если обработчик событий <xref:System.Windows.FrameworkElement.Loaded> уже существует, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] добавляет этот код в существующий обработчик событий.  
  
### Модели EDM  
 При перетаскивании сущности или свойства сущности из окна **Источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который выполняет следующие действия:  
  
-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент.  <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в сущности.  
  
-   Создание привязки данных для элемента управления.  Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] привязывает элемент управления к этому элементу.  Если перетащить элемент на контейнер, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к этому элементу.  Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
 Кроме того, Visual Studio вносит следующие изменения в файл кода программной части:  
  
-   Добавляет новый метод, который возвращает запрос для сущности, которую пользователь перетащил в конструктор \(или сущности, содержащей свойство, которое пользователь перетащил в конструктор\).  Имя нового метода — Get*EntityName*Query, где *EntityName* — это имя сущности.  
  
-   Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)], который содержит элемент управления.  Обработчик событий вызывает метод Get*EntityName*Query для наполнения сущности данными, получает <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом.  Если обработчик событий <xref:System.Windows.FrameworkElement.Loaded> уже существует, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] добавляет этот код в существующий обработчик событий.  
  
### Службы  
 При перетаскивании объекта или свойства службы из окна **Источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] генерирует [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который создает связанный с данными элемент управления \(либо создает привязку существующего элемента управления к этому объекту или свойству\).  Однако [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не создает код, который наполнил бы прокси\-объект службы данными.  Этот код придется написать самостоятельно.  Пример, демонстрирующий написание кода, см.в разделе [Пошаговое руководство. Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio создает язык XAML, который выполняет следующие действия:  
  
-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент.  <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте, возвращаемом службой.  
  
-   Создание привязки данных для элемента управления.  Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] привязывает элемент управления к этому элементу.  Если перетащить элемент на контейнер, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к этому элементу.  Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
### Объекты  
 При перетаскивании объекта или свойства из окна **Источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] генерирует [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который создает связанный с данными элемент управления \(либо создает привязку существующего элемента управления к этому объекту или свойству\).  Однако [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не создает код для наполнения объекта данными.  Этот код придется написать самостоятельно.  
  
> [!NOTE]
>  Пользовательский класс должен быть открытым и должен содержать конструктор по умолчанию без параметров.  Это не могут быть вложенные классы, которые записываются через точку.  Дополнительные сведения см. в разделе [Код XAML и пользовательские классы для WPF](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который выполняет следующие действия.  
  
-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент.  <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте.  
  
-   Создание привязки данных для элемента управления.  Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу.  Если перетащить элемент на контейнер, язык XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к этому элементу.  Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
## См. также  
 [Практическое руководство. Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Практическое руководство. Создание таблиц подстановки в приложениях WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Практическое руководство. Отображение связанных данных в приложениях WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Binding WPF Controls to an Entity Data Model \(Привязка элементов управления WPF к модели EDM\)](http://msdn.microsoft.com/data/jj574514.aspx)   
 [Пошаговое руководство. Привязка элементов управления WPF к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Пошаговое руководство. Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Пошаговое руководство. Отображение связанных данных в приложении WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [окно "Источники данных"](../Topic/Data%20Sources%20Window.md)   
 [Общие сведения об источниках данных](../data-tools/add-new-data-sources.md)