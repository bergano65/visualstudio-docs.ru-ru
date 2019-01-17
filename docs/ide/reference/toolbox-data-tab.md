---
title: Панель элементов, вкладка "Данные"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9e23cd79510d789c8c8f8b426fb3196f1845745
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952965"
---
# <a name="toolbox-data-tab"></a>Панель элементов, вкладка "Данные"

Отображение объектов данных, которые можно добавлять в формы и компоненты. Вкладка **Данные** **панели элементов** появляется при создании проекта, для которого есть связанный конструктор. **Панель элементов** по умолчанию отображается в интегрированной среде разработки Visual Studio; чтобы открыть **панель элементов**, выберите в меню **Вид** пункт **Панель элементов**.

> [!TIP]
> Запуск мастера настройки источников данных позволяет автоматически создать и настроить большинство элементов данных. Дополнительные сведения см. в разделе [Добавление новых источников данных](../../data-tools/add-new-data-sources.md).

## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса

Чтобы перейти непосредственно на страницу справочника по .NET Framework для конкретного компонента, нажмите клавишу **F1** для элемента на **панели элементов** или для элемента компонента в области конструктора.

|name|Описание|
|----------|-----------------|
|<xref:System.Data.DataSet>|Добавляет экземпляр типизированного или нетипизированного набора данных в форму или компонент. При перетаскивании объекта в конструктор отображается диалоговое окно, которое позволяет выбрать существующий класс типизированного набора данных или указать, что требуется создать новый, пустой, нетипизированный набор данных. **Примечание.**  Объект <xref:System.Data.DataSet> не используется на **панели элементов** для создания схемы и класса типизированного набора данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../../data-tools/create-and-configure-datasets-in-visual-studio.md).|
|<xref:System.Windows.Forms.DataGridView>|Обеспечивает эффективный и гибкий способ отображения данных в табличном формате.|
|<xref:System.Windows.Forms.BindingSource>|Упрощает процесс привязки элементов управления к базовому источнику данных.|
|<xref:System.Windows.Forms.BindingNavigator>|Представляет пользовательский интерфейс для перехода и обработки для элементов управления в форме, которые привязываются к данным.|

## <a name="see-also"></a>См. также раздел

- [Доступ к данным в Visual Studio](../../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio Data Tools для .NET](../../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Инструменты для работы с наборами данных в Visual Studio](../../data-tools/dataset-tools-in-visual-studio.md)
- [Привязка элементов управления к данным в Visual Studio](../../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Изменение данных в наборах данных](../../data-tools/edit-data-in-datasets.md)
- [Проверка данных в наборах данных](../../data-tools/validate-data-in-datasets.md)