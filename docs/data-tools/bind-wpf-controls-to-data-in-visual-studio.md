---
title: Привязка элементов управления WPF к данным в Visual Studio — часть 1 | Документы Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7674656c9a4995b853753e12b19fd71bf77a3c9f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926749"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Привязка элементов управления WPF к данным в Visual Studio
Для пользователей приложения данные можно отображать путем привязки данных к элементам управления [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Чтобы создать эти элементы управления с привязкой к данным, можно перетаскивать элементы из **источники данных** окна на [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В этом разделе описываются некоторые из наиболее распространенных задач, инструментов и классов, которые можно использовать для создания связанных с данными приложений [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)].

 Общие сведения о создании элементов управления с привязкой к данным в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], в разделе [привязки элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Дополнительные сведения о [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] в разделе [Общие сведения о привязке данных](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Задачи, решаемые в процессе привязки элементов управления WPF к данным
 В следующей таблице перечислены задачи, которые могут быть решены путем перетаскивания элементов из **источники данных** окна [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Задача|Дополнительные сведения|
|----------|----------------------|
|Создание новых элементов управления, связанных с данными<br /><br /> Привязка существующих элементов управления к данным|[Привязка элементов управления WPF к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Создание элементов управления, отображающих связанные данные в иерархическом отношении: когда пользователь выбирает родительскую запись данных в одном элементе управления, другой элемент управления отображает связанные дочерние данные для выбранной записи|[Отображение связанных данных в приложениях WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Создание *таблицы подстановки* , отображает информацию из одной таблицы на основе значения поля внешнего ключа в другой таблице.|[Создание таблиц подстановки в приложениях WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Привязка элемента управления к изображению в базе данных|[Привязка элементов управления к рисункам из базы данных](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Допустимые целевые объекты перетаскивания
 Можно перетаскивать элементы в **источники данных** только на допустимые целевые объекты перетаскивания в [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Имеется две основных разновидности допустимых конечных расположений сброса: контейнеры и элементы управления. Контейнер — это элемент пользовательского интерфейса, который обычно содержит элементы управления. Например, сетка является контейнером, равно как и окно.

## <a name="generated-xaml-and-code"></a>Созданный язык XAML и код
 При перетаскивании элемента из **источники данных** окна [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , определяет новый элемент управления с привязкой к данным (либо создает привязку существующего элемента управления к источнику данных). Для некоторых источников данных [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] также создает код в файле кода программной части, который наполняет данными источник данных.

 В следующей таблице перечислены [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] и кода, который [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводит к возникновению ошибки для каждого типа источника данных в **источники данных** окна.

|Источник данных|Создание языка XAML, который привязывает элемент управления к источнику данных|Создание кода, который заполняет данными источник данных|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Набор данных|Да|Да|
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Да|Да|
|Служба|Да|Нет|
|Object|Да|Нет|

### <a name="datasets"></a>Наборы данных
 При перетаскивании таблицы или столбца из **источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , который выполняет следующее:

-   Добавление набора данных и нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в наборе данных.

-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, язык XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

Кроме того, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] вносит следующие изменения в файл кода программной части:

-   Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)], который содержит элемент управления. Обработчик событий наполняет таблицу данными, извлекает <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом. Если <xref:System.Windows.FrameworkElement.Loaded> обработчик событий уже существует, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] добавляет этот код в существующий обработчик событий.

### <a name="entity-data-models"></a>Модели EDM
 При перетаскивании сущности или свойства сущности из **источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , который выполняет следующее:

-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в сущности.

-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

Кроме того, Visual Studio вносит следующие изменения в файл кода программной части:

-   Добавляет новый метод, который возвращает запрос для сущности, которую пользователь перетащил в конструктор (или сущности, содержащей свойство, которое пользователь перетащил в конструктор). Новый метод с именем Get*EntityName*запроса, где *EntityName* имя сущности.

-   Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)], который содержит элемент управления. Обработчик событий вызывает Get*EntityName*запроса метода для наполнения сущности данными, извлекает <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом. Если <xref:System.Windows.FrameworkElement.Loaded> обработчик событий уже существует, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] добавляет этот код в существующий обработчик событий.

### <a name="services"></a>Службы
 При перетаскивании объекта или свойства службы из **источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , создается элемент управления с привязкой к данным (либо создает привязку существующего элемента управления к объекту или свойству). Однако [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не создает код, который наполнил бы прокси-объект службы данными. Этот код придется написать самостоятельно. Пример, демонстрирующий, как это сделать см. в разделе [WPF привязать элементы управления к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio создает язык XAML, который выполняет следующие действия:

-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте, возвращаемом службой.

-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Объекты
 При перетаскивании объекта или свойства из **источники данных** в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , создается элемент управления с привязкой к данным (либо создает привязку существующего элемента управления к объекту или свойству). Однако [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не создает код для наполнения объекта данными. Этот код придется написать самостоятельно.

> [!NOTE]
>  Пользовательские классы должны быть открытыми и, по умолчанию иметь конструктор без параметров. Они can'tbe вложенные классы, которые имеют «точка» в их синтаксисе. Дополнительные сведения см. в разделе [XAML и пользовательские классы для WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводит к возникновению ошибки [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , который выполняет следующее:

-   Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте.

-   Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу. Если перетащить элемент на контейнер, язык XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)