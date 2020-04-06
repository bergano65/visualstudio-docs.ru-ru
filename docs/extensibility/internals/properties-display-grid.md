---
title: Свойства Дисплей сетки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706186"
---
# <a name="properties-display-grid"></a>Свойства отображения сетки

Окно **Свойства** отображает поля внутри сетки. Левая колонка содержит имена свойств; правый столбец содержит значения свойств.

## <a name="work-with-the-grid"></a>Работа с сеткой

В списке из двух столбцов показаны независящие от конфигурации свойства, которые могут быть изменены во время проектирования и их текущие параметры. Обратите внимание, что все свойства могут не отображаться. Свойство может быть установлено как скрытое, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> например, путем реализации метода. В частности, чтобы скрыть свойства, которые имеют свойства ребенка:

1. Установите `pfDisplay` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> `FALSE`.

2. Установите `pfHide` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> `TRUE`.

Чтобы донести информацию до окна <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> **Properties,** IDE использует . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>называется VSPackages для каждого окна, содержащего выбранные объекты со связанными свойствами, отображаемыми в окне **Свойств.** **Реализация**вызовов <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` Solution Explorer с использованием [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) в иерархии проектов для приобретения просматриваемых объектов в иерархии.

Если ваш VSPackage не поддерживает [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), IDE пытается <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> использовать значение для [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) что элемент иерархии или элементы поставляются.

Ваш проект VSPackage не <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> нужно создавать, потому что пакет окон, поставляемых IDE, который реализует его (например, **Solution Explorer)** строится <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>состоит из трех методов, которые называются IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>содержит количество объектов, выбранных для отображения в окне **Свойств.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>возвращает `IDispatch` выбранные объекты для отображения в окне **свойств.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>позволяет любому из объектов, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> возвращенных пользователем, быть выбранным пользователем. Это позволяет VSPackage визуально обновить выбор, отображаемый для пользователя в пользовательском интерфейсе.

Окно **Свойства** извлекает информацию из объектов `IDispatch` для получения просматриваемых свойств. Браузер Properties `IDispatch` использует, чтобы спросить объект, какие `ITypeInfo`свойства он поддерживает, запрашивая, который получен из. `IDispatch::GetTypeInfo` Затем браузер использует эти значения для заполнения окна **Свойств** и изменения значений для отдельных свойств, отображаемых в сетке. Информация о свойствах сохраняется внутри самого объекта.

Поскольку возвращенные `IDispatch`объекты поддерживаются, абонент может получить информацию, `IDispatch::Invoke` `ITypeInfo::Invoke` такую как имя объекта, позвонив либо, либо с помощью заданного идентификатора диспетчерской рассылки (DISPID), представляющего нужную информацию. Объявленные DISPID являются отрицательными, чтобы убедиться, что они не противоречат пользовательским идентификаторам.

Окно **Свойства** отображает различные типы полей в зависимости от атрибутов определенных свойств выбранного объекта. Эти поля включают в себя редитивные коробки, списки выпадающих и ссылки на пользовательские диалоговые ящики редактора.

- Значения, содержащиеся в перечисленном списке, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> извлекаются `IDispatch`запросом на запрос. Значения, полученные из перечисленного списка, могут быть изменены в сетке свойств, дважды нажав на имя поля, или нажав на значение и выбрав новое значение из списка выпадающих. Для свойств, которые предопределили параметры из перечисленных списков, двойное нажатие имени свойства в списке свойств циклов через доступные варианты. Для предопределенных свойств только с двумя вариантами, такими как true/false, дважды щелкните имя свойства, чтобы переключаться между выборами.

- Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`это означает, что значение было изменено, значение отображается жирным текстом. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>используется для определения того, можно ли сбросить значение в исходное значение. Если это так, вы можете изменить обратно по умолчанию, нажав на стоимость и выбрав **сбросить** из отображаемого меню. В противном случае необходимо изменить значение обратно на значение по умолчанию вручную. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>также позволяет локализовать и скрыть имена свойств, отображаемых во время проектирования, но не влияет на имена свойств, отображаемые во время выполнения.

- Нажатие кнопки ellipsis (...) отображает список значений свойств, из которых пользователь может выбрать (например, список сборщиков цветов или список шрифтов). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>обеспечивает эти значения.

## <a name="see-also"></a>См. также

- [Расширить свойства](../../extensibility/internals/extending-properties.md)
