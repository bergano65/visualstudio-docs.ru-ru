---
title: Расширение свойств | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d03533679e367afb1f50ee55196c5d96e03ae580
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846589"
---
# <a name="extend-properties"></a>Расширение свойств
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Свойства** окно браузер универсальных свойств для компонентов COM и COM + и поддерживает все [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] продуктов. **Свойства** окно работает с `ITypeInfo` введите сведения и метаданные COM +, чтобы перечислить свойства времени разработки для текущего выбранного объекта в любое другое окно в интегрированной среде разработки (IDE).  
  
 **Свойства** окно, которое можно открыть, нажав клавишу **F4** на клавиатуре или выбрав **окно "Свойства"** на **представление** меню используется для просмотра и изменения свойства, зависящие от конфигурации, разработки и события выбранных объектов. Свойства, зависящие от конфигурации, связанные с решениями и проектами, которые отображаются на [страницы свойств](../../extensibility/internals/property-pages.md). Дополнительные сведения [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Общие сведения об окне свойств](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Окно \"Свойства\"  
  
 Этот раздел содержит подробные сведения, относящиеся к отдельным областям **свойства** окна и интерфейсы, которые необходимо реализовать и вызова для заполнения окна.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Общие сведения об окне свойств](../../extensibility/internals/properties-window-overview.md)  
 Описание назначения **свойства** окна относительно окна инструментов и окна документа.  
  
 [Шаблон политики и окне «Свойства»](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Рассматривается как проект находится в корпоративном проекте шаблона, а также как требовать использование политики для этого проекта шаблона предприятия.  
  
 [Поля окна свойств и интерфейсы](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Объясняет основы для выбора, который определяет, какие данные будут отображаться в **свойства** окна.  
  
 [Список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md)  
 Описывает цель **свойства** список объектов окна, описывающий, как это сделать, при активации вызов другой объект из этого списка среды уведомляется о том, что объект был выбран.  
  
 [Кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md)  
 Описание назначения по умолчанию четыре кнопки, отображаемые на **свойства** окна инструментов.  
  
 [Отображение сетки свойств](../../extensibility/internals/properties-display-grid.md)  
 Объясняется, где имена свойств и поля значений свойств можно найти в сетке.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Рассматривается проектов как составными частями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 [Компиляция и сборка](../../ide/compiling-and-building-in-visual-studio.md)  
 Описывается, как можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] платформы для непрерывного тестирования и отладки приложений в ходе их построения.  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 Описывает `IDispatch` интерфейс, который сначала был разработан для поддержки автоматизации, предоставляя механизм для доступа и получить сведения о методах и свойствах объекта с поздним связыванием.  
  
 [Управление параметрами приложения (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Обзор параметров приложения, которые позволяют настроить приложение таким образом, чтобы значения свойств хранятся в внешнего файла конфигурации вместо скомпилированный код приложения.  
  
 [Проекты и решения](../../ide/solutions-and-projects-in-visual-studio.md)  
 Объясняет, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] эффективно управляет элементов, таких как ссылки, подключения к данным, папки и файлы, которые необходимы на этапе разработки через решения и проекты.  
  
 [Расширение других частей Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Объясняется использование служб [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].