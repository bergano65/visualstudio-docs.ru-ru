---
title: Интерфейс пользователя свойств проекта (ru) Документы Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706395"
---
# <a name="project-property-user-interface"></a>Пользовательский интерфейс свойств проекта

Подтип проекта может использовать элементы в диалоговом поле страниц **свойств** проекта, поскольку они поставляются базовым проектом, скрывать или делать только элементы управления и целые страницы в виде поставляемых или добавлять страницы, связанные с подтипом проекта, в диалоговую базу **«Страницы свойств».**

## <a name="extending-the-project-property-dialog-box"></a>Расширение коробки диалогов свойств проекта

Подтип проекта реализует расширители автоматизации и объекты просмотра конфигурации проекта. Эти расширители реализуют <xref:EnvDTE.IFilterProperties> интерфейс, чтобы сделать определенные свойства скрытыми или только для чтения. Диалоговая коробка **«Страницы свойств»** базового проекта, реализуемая базовым проектом, чтит фильтрацию, выполняемую удлинителями автоматизации.

Процесс расширения диалогового окна **Project Property** описан ниже:

- Базовый проект извлекает расширители из подтипа <xref:EnvDTE80.IInternalExtenderProvider> проекта путем реализации интерфейса. Просмотр, автоматизация проекта и конфигурация проекта просматривают объекты базового проекта, реализуя этот интерфейс.

- Реализация <xref:EnvDTE80.IInternalExtenderProvider> для объекта просмотра проекта и делегирование <xref:EnvDTE80.IInternalExtenderProvider> объекта автоматизации проекта до реализации агрегатора `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> подтипа <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> проекта (то есть они для на объекте проекта).

- Объект просмотра конфигурации <xref:EnvDTE80.IInternalExtenderProvider> базового проекта также реализуется непосредственно в расширитель автоматизации от объекта конфигурации подтипа проекта. Его реализация делегирует <xref:EnvDTE80.IInternalExtenderProvider> интерфейс, реализованный агрегатором подтипа проекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, реализованная конфигурацией проекта просматривать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объект, возвращает объект.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, также реализованный конфигурацией проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> просматривать объект, возвращает объект.

- Подтип проекта может определить соответствующие CATID для различных расширяемых объектов <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> базового проекта во время выполнения, извлекая следующие значения:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Чтобы определить CATID для области проекта, подтип проекта получает вышеуказанные свойства для [VSITEMID. Корень](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) из `VSITEMID typedef`. Подтип проекта может также захотеть контролировать, какие страницы диалогового окна **Страницы свойств** отображаются для проекта, как зависимые от конфигурации, так и независимые конфигурации. Некоторым подтипам проекта может потребоваться удалить встроенные страницы и добавить определенные страницы подтипа проекта. Для этого управляемый клиентский проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> называет метод для следующих свойств:

- `VSHPROPID_PropertyPagesCLSIDList`— список CLSID, не зависят от конфигурации.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`список CLSID, зависящих от конфигурации страниц свойств.

Поскольку подтип проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> агрегирует объект, он может переопределить определение этих свойств, чтобы контролировать, какие диалоговые **ящики Страниц свойств** отображаются. Подтип проекта может извлечь эти свойства из внутреннего базового проекта, а затем добавить или удалить CLSID s по мере необходимости.

Новые страницы свойств, добавленные подтипом проекта, передаются объекту просмотра конфигурации проекта из реализации базового проекта. Этот объект просмотра конфигурации проекта поддерживает расширители автоматизации. Для получения дополнительной информации [Implementing and Using Automation Extenders](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)об AutomationExtenders см. Страницы свойств, реализованные вызовом <xref:EnvDTE.Project.Extender%2A> подтипа проекта для получения собственного объекта подтипа проекта, расширяем объект просмотра конфигурации базового проекта.

## <a name="see-also"></a>См. также

- <xref:EnvDTE.IFilterProperties>
- [Страницы свойств Диалог Box](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
