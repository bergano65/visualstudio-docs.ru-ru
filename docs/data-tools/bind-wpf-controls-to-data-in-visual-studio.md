---
title: Привязка элементов управления WPF к данным — часть 1
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ee858c7c17798f327d323f632d4cb9e8a77b6712
ms.sourcegitcommit: bde55773485c9bca50a760ac9e4c919e0a208a51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72924528"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Привязка элементов управления WPF к данным в Visual Studio

Для пользователей приложения данные можно отображать путем привязки данных к элементам управления [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Чтобы создать эти элементы управления с привязкой к данным, можно перетащить элементы из окна **Источники данных** на [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] в Visual Studio. В этом разделе описываются некоторые из наиболее распространенных задач, инструментов и классов, которые можно использовать для создания связанных с данными приложений [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)].

Общие сведения о создании элементов управления с привязкой к данным в Visual Studio см. [в разделе Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Дополнительные сведения о привязке данных [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] см. в разделе [Общие сведения о привязке данных](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Задачи, решаемые в процессе привязки элементов управления WPF к данным

В следующей таблице перечислены задачи, которые могут быть решены путем перетаскивания элементов из окна **Источники данных** в [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Задача|Дополнительные сведения|
|----------| - |
|Создание новых элементов управления, связанных с данными<br /><br /> Привязка существующих элементов управления к данным|[Привязка элементов управления WPF к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Создание элементов управления, отображающих связанные данные в иерархическом отношении: когда пользователь выбирает родительскую запись данных в одном элементе управления, другой элемент управления отображает связанные дочерние данные для выбранной записи|[Отображение связанных данных в приложениях WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Создание *таблицы подстановки*, которая отображает информацию из одной таблицы на основе значения в поле внешнего ключа в другой таблице.|[Создание таблиц подстановки в приложениях WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Привязка элемента управления к изображению в базе данных|[Привязка элементов управления к рисункам из базы данных](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Допустимые места переноса

Элементы в окне **Источники данных** можно перетаскивать только на допустимые места переноса в [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Имеется две основных разновидности допустимых конечных расположений сброса: контейнеры и элементы управления. Контейнер — это элемент пользовательского интерфейса, который обычно содержит элементы управления. Например, сетка является контейнером, равно как и окно.

## <a name="generated-xaml-and-code"></a>Созданный язык XAML и код

При перетаскивании элемента из окна « **Источники данных** » в [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]Visual Studio создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который определяет новый элемент управления с привязкой к данным (или привязывает существующий элемент управления к источнику данных). Для некоторых источников данных Visual Studio также создает код в файле кода программной части, который заполняет источник данных данными.

В следующей таблице перечислены [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] и код, создаваемый Visual Studio для каждого типа источника данных в окне **Источники данных** .

| Источник данных | Создание языка XAML, который привязывает элемент управления к источнику данных | Создание кода, который заполняет данными источник данных |
| - | - | - |
| Набор данных | Да | Да |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Да | Да |
| Служба | Да | Нет |
| Object | Да | Нет |

### <a name="datasets"></a>Наборы данных

При перетаскивании таблицы или столбца из окна **Источники данных** в конструктор Visual Studio создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который выполняет следующие действия:

- Добавление набора данных и нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в наборе данных.

- Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу. При перетаскивании элемента в контейнер XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

Кроме того, Visual Studio вносит следующие изменения в файл кода программной части:

- Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)], который содержит элемент управления. Обработчик событий наполняет таблицу данными, извлекает <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом. Если обработчик событий <xref:System.Windows.FrameworkElement.Loaded> уже существует, Visual Studio добавляет этот код в существующий обработчик событий.

### <a name="entity-data-models"></a>Модели EDM

При перетаскивании сущности или свойства сущности из окна **Источники данных** в конструктор Visual Studio создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который выполняет следующие действия:

- Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в сущности.

- Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] привязывает элемент управления к этому элементу. При перетаскивании элемента в контейнер [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

Кроме того, Visual Studio вносит следующие изменения в файл кода программной части:

- Добавляет новый метод, который возвращает запрос для сущности, которую пользователь перетащил в конструктор (или сущности, содержащей свойство, которое пользователь перетащил в конструктор). Новый метод имеет имя `Get<EntityName>Query`, где `\<EntityName>` — имя сущности.

- Создает обработчик событий <xref:System.Windows.FrameworkElement.Loaded> для элемента [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)], который содержит элемент управления. Обработчик событий вызывает метод `Get<EntityName>Query` для заполнения сущности данными, извлекает <xref:System.Windows.Data.CollectionViewSource> из ресурсов контейнера, а затем делает первый элемент данных текущим элементом. Если обработчик событий <xref:System.Windows.FrameworkElement.Loaded> уже существует, Visual Studio добавляет этот код в существующий обработчик событий.

### <a name="services"></a>Службы

При перетаскивании объекта или свойства службы из окна **Источники данных** в конструктор Visual Studio создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который создает элемент управления с привязкой к данным (или привязывает существующий элемент управления к объекту или свойству). Однако Visual Studio не создает код, который заполняет объект прокси-службы данными. Этот код придется написать самостоятельно. Пример, демонстрирующий это, см. в разделе [Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio создает язык XAML, который выполняет следующие действия:

- Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте, возвращаемом службой.

- Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] привязывает элемент управления к этому элементу. При перетаскивании элемента в контейнер [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Объекты

При перетаскивании объекта или свойства из окна **Источники данных** в конструктор Visual Studio создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который создает элемент управления с привязкой к данным (или привязывает существующий элемент управления к объекту или свойству). Однако Visual Studio не создает код для заполнения объекта данными. Этот код придется написать самостоятельно.

> [!NOTE]
> Пользовательские классы должны быть открытыми и, по умолчанию, иметь конструктор без параметров. Они не могут быть вложенными классами, в синтаксисе которых есть точка. Дополнительные сведения см. в разделе [XAML и пользовательские классы для WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio создает [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], который выполняет следующие действия:

- Добавление нового <xref:System.Windows.Data.CollectionViewSource> в ресурсы контейнера, на который пользователь перетащил элемент. <xref:System.Windows.Data.CollectionViewSource> — это объект, который можно использовать для навигации и отображения данных в объекте.

- Создание привязки данных для элемента управления. Если перетащить элемент на существующий элемент управления в конструкторе, язык XAML привязывает элемент управления к этому элементу. При перетаскивании элемента в контейнер XAML создает элемент управления, который был выбран для перетаскиваемого элемента, и привязывает элемент управления к элементу. Элемент управления создается внутри нового <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
