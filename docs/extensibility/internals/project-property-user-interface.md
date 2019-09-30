---
title: Пользовательский интерфейс свойства проекта | Документация Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a83e5c9fb633322da536e62f1ba03484b965b162
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252359"
---
# <a name="project-property-user-interface"></a>Пользовательский интерфейс свойств проекта

Подтип проекта может использовать элементы в диалоговом окне **страницы свойств** проекта в том виде, в каком они предоставляются базовым проектом, скрывать или делать элементы управления только для чтения и целые страницы как предоставленные, а также добавлять страницы для конкретных подтипов проектов в диалоговое окно **страницы свойств** . Box.

## <a name="extending-the-project-property-dialog-box"></a>Расширение диалогового окна «Свойства проекта»

Подтип проекта реализует расширители автоматизации и объекты обзора конфигурации проекта. Эти расширители реализуют <xref:EnvDTE.IFilterProperties> интерфейс, чтобы сделать конкретные свойства скрытыми или только для чтения. Диалоговое окно **страницы свойств** базового проекта, реализуемого базовым проектом, учитывает фильтрацию, выполняемую расширителями автоматизации.

Процесс расширения диалогового окна **свойств проекта** описан ниже.

- Базовый проект получает расширители из подтипа проекта путем реализации <xref:EnvDTE80.IInternalExtenderProvider> интерфейса. Для просмотра объектов базового проекта в области Обзор, Автоматизация проекта и проект используйте этот интерфейс.

- Реализация <xref:EnvDTE80.IInternalExtenderProvider> для объекта "Обзор проекта" и делегата объекта автоматизации проекта <xref:EnvDTE80.IInternalExtenderProvider> для реализации агрегатора подтипа проекта `QueryInterface` (то есть для <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объект Project).

- Базовый объект "Обзор конфигурации проекта" также <xref:EnvDTE80.IInternalExtenderProvider> реализует прямую связь в расширителье автоматизации из объекта конфигурации подтипа проекта. Его реализация делегирует <xref:EnvDTE80.IInternalExtenderProvider> интерфейс, реализуемый агрегатором подтипа проекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, реализованный объектом обзора конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объект.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, также реализованный объектом обзора конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объект.

- Подтип проекта может определять подходящие CATID для различных расширяемых объектов базового проекта во время выполнения, получая следующие <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> значения:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Чтобы определить CATID для области проекта, подтип проекта получает указанные выше свойства для [вситемид. Корень](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) из `VSITEMID typedef`. Подтип проекта может также контролировать, какие страницы диалогового окна **свойств** будут отображаться для проекта, как зависимые от конфигурации, так и зависящие от конфигурации. Некоторым подтипам проекта может потребоваться удалить встроенные страницы и добавить определенные страницы для подтипов проектов. Чтобы сделать это, управляемый клиентский проект вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> метод для следующих свойств:

- `VSHPROPID_PropertyPagesCLSIDList`— Разделенный точками с запятой список идентификаторов CLSID страниц свойств, не зависящих от конфигурации.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`Разделенный точками с запятой список идентификаторов CLSID страниц свойств, зависящих от конфигурации.

Поскольку подтип проекта выполняет статистическую обработку <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта, он может переопределить определение этих свойств, чтобы управлять отображением диалоговых окон **страниц свойств** . Подтип проекта может извлекать эти свойства из внутреннего базового проекта, а затем добавлять или удалять идентификаторы CLSID по мере необходимости.

Новые страницы свойств, добавленные подтипом проекта, передаются в конфигурации проекта в качестве объекта обзора из базовой реализации проекта. Этот объект "Обзор" конфигурации проекта поддерживает расширители автоматизации. Дополнительные сведения о Аутоматионекстендерс см. в разделе [Реализация и использование расширителей автоматизации](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Страницы свойств, реализованные при вызове <xref:EnvDTE.Project.Extender%2A> подтипа проекта для получения собственного объекта "Обзор конфигурации подтипа проекта", который расширяет объект "Обзор конфигурации" базового проекта.

## <a name="see-also"></a>См. также

- <xref:EnvDTE.IFilterProperties>
- [Диалоговое окно «страницы свойств»](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
