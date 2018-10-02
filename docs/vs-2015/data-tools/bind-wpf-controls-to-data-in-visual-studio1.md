---
title: Привязка элементов управления WPF к данным в Visual Studio 1 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f07087ce1f7637e63bd2d99aeb2cb125265a2d22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571022"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Привязка элементов управления WPF к данным в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элементы управления WPF, привязка к данным в Visual Studio — часть 1 | Документация Microsoft](https://docs.microsoft.com/visualstudio/data-tools/bind-wpf-controls-to-data-in-visual-studio).  
  
  
Для пользователей приложения данные можно отображать путем привязки данных к элементам управления [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]. Чтобы создать эти элементы управления с привязкой к данным, можно перетаскивать элементы из **источников данных** окна на [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. В этом разделе описываются некоторые из наиболее распространенных задач, инструментов и классов, которые можно использовать для создания связанных с данными приложений [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)].  
  
 Общие сведения о том, как создавать элементы управления с привязкой к данным в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Дополнительные сведения о [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] привязки данных, см. в разделе [Общие сведения о привязке данных](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Задачи, решаемые в процессе привязки элементов управления WPF к данным  
 В следующей таблице перечислены задачи, которые могут быть решены путем перетаскивания элементов из **источников данных** окно, чтобы [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)].  
  
|Задача|Дополнительные сведения|  
|----------|----------------------|  
|Создание новых элементов управления, связанных с данными<br /><br /> Привязка существующих элементов управления к данным|[Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [элементы управления WPF, привязка к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|Создание элементов управления, отображающих связанные данные в иерархическом отношении: когда пользователь выбирает родительскую запись данных в одном элементе управления, другой элемент управления отображает связанные дочерние данные для выбранной записи|[Отображение связанных данных в приложениях WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Создание *таблицы подстановки* , отображающий сведения из одной таблицы на основе значения поля внешнего ключа в другой таблице.|[Создание таблиц подстановки в приложениях WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Привязка элемента управления к изображению в базе данных|[Привязка элементов управления к рисункам из базы данных](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## <a name="valid-drop-targets"></a>Допустимые конечные расположения сброса  
 Можно перетащить элементы **источников данных** окно только допустимые конечные расположения сброса в [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]. Имеется две основных разновидности допустимых конечных расположений сброса: контейнеры и элементы управления. Контейнер — это элемент пользовательского интерфейса, который обычно содержит элементы управления. Например, сетка является контейнером, равно как и окно.  
  
## <a name="generated-xaml-and-code"></a>Созданный XAML и кода  
 При перетаскивании элемента из **источников данных** окно, чтобы [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)], [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , определяет новый элемент управления с привязкой к данным (либо создает привязку существующего элемента управления к источнику данных). Для некоторых источников данных [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] также создает код в файле кода программной части, который наполняет данными источник данных.  
  
 В следующей таблице перечислены [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] и кода, который [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] создает для каждого типа источника данных в **источников данных** окна.  
  
|Источник данных|Создание языка XAML, который привязывает элемент управления к источнику данных|Создание кода, который заполняет данными источник данных|  
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|  
|Набор данных|Да|Да|  
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Да|Да|  
|Служба|Да|Нет|  
|Object|Да|Нет|  
  
### <a name="datasets"></a>Наборы данных  
 При перетаскивании таблицы или столбца из **источников данных** окно в конструктор [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , выполняет следующие:  
  
-   Добавление набора данных и нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в наборе данных.  
  
-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
 Кроме того, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] вносит следующие изменения в файл кода программной части:  
  
-   Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)], который содержит элемент управления. Обработчик событий наполняет таблицу данными, извлекает <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом. Если <xref:System.Windows.FrameworkElement.Loaded> обработчик событий уже существует, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] добавляет этот код в существующий обработчик событий.  
  
### <a name="entity-data-models"></a>Модели EDM  
 При перетаскивании сущности или свойства сущности из **источников данных** окно в конструктор [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , выполняет следующие:  
  
-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в сущности.  
  
-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
 Кроме того, Visual Studio вносит следующие изменения в файл кода программной части:  
  
-   Добавляет новый метод, который возвращает запрос для сущности, которую пользователь перетащил в конструктор (или сущности, содержащей свойство, которое пользователь перетащил в конструктор). Новый метод имеет имя Get*EntityName*запроса, где *EntityName* имя сущности.  
  
-   Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)], который содержит элемент управления. Обработчик событий вызывает Get*EntityName*метод для наполнения сущности данными, извлекает запроса <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом. Если <xref:System.Windows.FrameworkElement.Loaded> обработчик событий уже существует, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] добавляет этот код в существующий обработчик событий.  
  
### <a name="services"></a>Службы  
 При перетаскивании объекта или свойства службы из **источников данных** окно в конструктор [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , создает элемент управления с привязкой к данным (либо создает привязку существующего элемента управления к объекту или свойству). Однако [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не создает код, который наполнил бы прокси-объект службы данными. Этот код придется написать самостоятельно. Пример, в котором показано, как это сделать, см. в разделе [элементы управления WPF, привязка к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio создает язык XAML, который выполняет следующие действия:  
  
-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте, возвращаемом службой.  
  
-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
### <a name="objects"></a>Объекты  
 При перетаскивании объекта или свойства из **источников данных** окно в конструктор [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , создает элемент управления с привязкой к данным (либо создает привязку существующего элемента управления к объекту или свойству). Однако [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не создает код для наполнения объекта данными. Этот код придется написать самостоятельно.  
  
> [!NOTE]
>  Пользовательские классы должны быть открытыми и, по умолчанию имеют конструктор без параметров. Они can'tbe вложенные классы, которые имеют «точка» в их синтаксис. Дополнительные сведения см. в разделе [XAML и пользовательские классы для WPF](http://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Создает [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , делает следующее:  
  
-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте.  
  
-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

