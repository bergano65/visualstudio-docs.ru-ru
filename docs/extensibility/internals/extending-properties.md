---
title: Расширяющие свойства (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708417"
---
# <a name="extend-properties"></a>Расширить свойства
Окно [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Properties** является универсальным браузером свойств для компонентов COM и COM и поддерживает все [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] продукты. Окно **Свойства** работает `ITypeInfo` с информацией о типе и метаданными КОМЗ, чтобы перечислить свойства времени проектирования для выбранного объекта в любом другом окне в интегрированной среде разработки (IDE).

 Окно **Properties,** которое может быть открыто нажатием **F4** на клавиатуре или выбрав **окно свойств** в меню **View,** используется для просмотра и отображания независящих от конфигурации, свойств времени проектирования и событий выбранных объектов. Зависящие от конфигурации свойства, связанные с решениями и проектами, отображаются на [страницах Property.](../../extensibility/internals/property-pages.md) Для получения дополнительной [информации, Управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).

 ![Обзор окна свойств](../../extensibility/internals/media/vspropertieswindow.png "vsСвойстваОкно") Окно свойств

 В этом разделе содержится подробная информация, относящаяся к отдельным областям окна **Свойств** и интерфейсам, которые необходимо реализовать, и вызову для заполнения окна.

## <a name="in-this-section"></a>В этом разделе
- [Обзор окна свойств](../../extensibility/internals/properties-window-overview.md)

 Объясняет назначение окна **Свойств** относительно окна инструмента и окна документа.

- [Политика шаблонов и окно свойств](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Обсуждается, как проект содержится в проекте шаблона предприятия, и как этот проект шаблона предприятия может обеспечить выполнение политики.

- [Свойства оконных полей и интерфейсов](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Объясняет основу для выбора, определяющую, какая информация отображается в окне **Свойств.**

- [Список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md)

 Описывает назначение списка объектов окна **Свойств,** описывая, как, когда другой объект из этого списка запускает вызов, среда информируется о том, что выбран новый объект.

- [Кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md)

 Объясняет назначение четырех кнопок по умолчанию, отображаемых на панели инструментов окна **Properties.**

- [Свойства отображения сетки](../../extensibility/internals/properties-display-grid.md)

 Объясняет, где в сетке находятся имена свойств и поля значений свойств.

## <a name="related-sections"></a>См. также
- [Типы проектов](../../extensibility/internals/project-types.md)

 Обсуждается проекты как строительные блоки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Компиляция и сборка](../../ide/compiling-and-building-in-visual-studio.md)

 Описывает, как можно [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использовать платформу для непрерывного тестирования и отладки приложений при их создании.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Описывает `IDispatch` интерфейс, который был впервые разработан для поддержки автоматизации, обеспечивая механизм с опозданием для доступа и получения информации о методах и свойствах объекта.

- [Управление параметрами приложения (.NET)](../../ide/managing-application-settings-dotnet.md)

 Предоставляет обзор настроек приложения, которые позволяют настроить приложение таким образом, чтобы значения свойств хранились во внешнем файле конфигурации вместо компилированного кода приложения.

- [Проекты и решения](../../ide/solutions-and-projects-in-visual-studio.md)

 Объясняет, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] насколько эффективно управление такими элементами, как ссылки, соединения данных, папки и файлы, необходимые для разработки через решения и проекты.

- [Расширить другие части Визуальной студии](../../extensibility/extending-other-parts-of-visual-studio.md)

 Объясняется использование служб [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
