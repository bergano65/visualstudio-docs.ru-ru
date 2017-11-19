---
title: "Расширение свойств | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: abf254aa21be5ec4b7401e21afa5f9bcca00e011
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="extending-properties"></a>Расширение свойств
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Свойства** окна браузера универсальных свойств для компонентов COM и COM + и поддерживает все [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] продуктов. **Свойства** окно работает с `ITypeInfo` введите сведения и метаданные COM +, чтобы вывести список свойств во время разработки для выбранного объекта в любое другое окно интегрированной среды разработки (IDE).  
  
 **Свойства** окно, которое можно открыть, нажав F4 на клавиатуре или выбрав **окно свойств** на **представление** меню, используется для просмотра и редактирования зависящие от конфигурации, во время разработки свойства и события выбранных объектов. Свойства, зависящие от конфигурации, связанные с решениями и проектами, отображаются на [страницы свойств](../../extensibility/internals/property-pages.md). Дополнительные сведения см. в разделе [NIB: свойства](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md), и [NIB: управление элементами в проектах](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Общие сведения об окне свойств](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Окно \"Свойства\"  
  
 Этот раздел содержит подробные сведения, относящиеся к отдельным областям **свойства** окна и интерфейсы, которые должны быть реализованы и вызова для заполнения окна.  
  
## <a name="in-this-section"></a>Содержание  
 [Общие сведения об окне свойств](../../extensibility/internals/properties-window-overview.md)  
 Описание назначения **свойства** окна относительно окна инструментов и окна документа.  
  
 [Шаблон политики и окно свойств](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Описывает, как проект содержится в корпоративном проекте шаблона и как этот проект шаблона предприятия могут применять политику.  
  
 [Поля окна свойств и интерфейсы](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Объясняет основы для выделения, которое определяет, какие данные будут отображаться в **свойства** окна.  
  
 [Список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md)  
 Описывает назначение **свойства** окна список объектов, описывающий, как это сделать, при вызове другой объект из этого списка, среды уведомляется о том, что был выбран новый объект.  
  
 [Кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md)  
 Описание назначения по умолчанию четыре кнопки, отображаемые на **свойства** окна инструментов.  
  
 [Отображение сетки свойств](../../extensibility/internals/properties-display-grid.md)  
 Объясняется, где найти имена свойств и полей значений свойств в сетку.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Описывает проекты как составными частями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 [Компилирование и сборка](../../ide/compiling-and-building-in-visual-studio.md)  
 Описывает, как можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] платформу для непрерывного тестирования и отладки приложений в ходе их построения.  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 Описывает `IDispatch` интерфейс, который сначала был разработан для поддержки автоматизации, предоставляя механизм позднего связывания для доступа и получать сведения о методы и свойства объекта.  
  
 [Управление параметрами приложения (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Общие параметры приложения, которые позволяют настроить приложение таким образом, чтобы значения свойств хранятся в внешнего файла конфигурации вместо скомпилированный код приложения.  
  
 [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)  
 Объясняет, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] эффективно управляет элементы, такие как ссылки, подключения к данным, папки и файлы, необходимые на этапе разработки через решений и проектов.  
  
 [Расширение других частей Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Описание способов использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] служб для создания элементов пользовательского интерфейса, которые соответствуют остальной части [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].