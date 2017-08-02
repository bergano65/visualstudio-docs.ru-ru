---
title: "Расширение свойства | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>Расширение свойств
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Свойства** окна Обозреватель универсальных свойств для компонентов COM и COM + и поддерживает все [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] продуктов. **Свойства** окно работает с `ITypeInfo` введите сведения и метаданные COM +, чтобы список свойств во время разработки для выбранного объекта в любом окне в интегрированную среду разработки (IDE).  
  
 **Свойства** окно, которое можно открыть, нажав F4 на клавиатуре или выбрав **окно свойств** на **представление** меню, используется для просмотра и изменения зависят от конфигурации, во время разработки свойства и события выбранных объектов. Свойства, зависящие от конфигурации, связанные с решениями и проектами, которые отображаются на [страницы свойств](../../extensibility/internals/property-pages.md). Дополнительные сведения см. в разделе [NIB: проект свойства](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md), и [NIB: элемент управления в проектах](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Общие сведения об окне свойств](~/docs/extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Окно \"Свойства\"  
  
 Этот раздел содержит подробные сведения, относящиеся к отдельным областям **свойства** окна и интерфейсы, которые необходимо реализовать и вызова для заполнения окна.  
  
## <a name="in-this-section"></a>Содержание  
 [Общие сведения об окне свойств](../../extensibility/internals/properties-window-overview.md)  
 Описание назначения **свойства** окна относительно окна инструментов и окна документа.  
  
 [Шаблон политики и окна свойств](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Описывает, как проект находится в шаблон корпоративного проекта, и как шаблона проекта, предприятия могут применять политику.  
  
 [Поля окна свойств и интерфейсы](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Объясняет основы для выбора, который определяет, какие данные будут отображаться в **свойства** окна.  
  
 [Список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md)  
 Описывает назначение **свойства** списка объектов в окне, описывающие, как, когда другой объект из этого списка инициирует вызов, среде о выбран новый объект.  
  
 [Кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md)  
 Описание назначения четыре стандартных кнопок, отображаемых на **свойства** окно инструментов.  
  
 [Отображение сетки свойств](../../extensibility/internals/properties-display-grid.md)  
 Объясняется, где найти имена свойств и полей значений свойств в сетку.  
  
 [Отслеживание выделения в окне свойств](../../misc/announcing-property-window-selection-tracking.md)  
 Описывает Выбор отслеживания для **свойства** окна.  
  
 [Скрытие свойств, имеющих дочерние свойства](../../misc/hiding-properties-that-have-child-properties.md)  
 Объясняется, как скрыть свойства, имеющие дочерние свойства путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [Предоставление пользовательского окна свойств](../../misc/providing-a-custom-properties-window.md)  
 Подробно описывает шаги для предоставления свойства браузера.  
  
 [Получение описаний полей из окна "Свойства"](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Объясняется, где можно найти в области описания, отображает сведения, связанные с полем выбранного свойства.  
  
 [Обновление значений свойств в окне "Свойства"](../../misc/updating-property-values-in-the-properties-window.md)  
 Пошаговые инструкции, которые показаны два способа сохранить **свойства** окно синхронизацию изменений, значение свойства.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Рассматривается как основой для построения проектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 [Компилирование и сборка](../../ide/compiling-and-building-in-visual-studio.md)  
 Описывает, как можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] платформу для непрерывного тестирования и отладки приложений в ходе их построения.  
  
 [Свойства документа HTML, окно свойств](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Инструкции для редактирования HTML-документа непосредственно из окна свойств, а таблица с подробным описанием полей в документе HTML в окне «Свойства».  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Описывает `IDispatch` интерфейс, который сначала был разработан для поддержки автоматизации, предоставляя механизм позднего связывания для доступа и извлечения сведений о методы и свойства объекта.  
  
 [NIB: Введение в динамические свойства (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Общие сведения о динамических свойств, которые позволяют настроить приложение таким образом, чтобы значения свойств хранятся в внешнего файла конфигурации вместо скомпилированный код приложения.  
  
 [NIB: проекты как контейнеры](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Описывает роль проекта как контейнер в решении, чтобы логически управления, построения и отладки элементов, составляющих приложение.  
  
 [NIB: свойства](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Описывает, как проект управляет параметрами, позволяющими свойства элемента управления, которые применяются для всего проекта, а также свойства, ограниченные определенными конфигурациями сборки проекта.  
  
 [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)  
 Объясняет, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] эффективно управляет элементы, такие как ссылки, подключения данных, папки и файлы, необходимые на этапе разработки до решений и проектов.  
  
 [Расширение других частей Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Описание способов использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] служб для создания элементов пользовательского интерфейса, которые соответствуют остальной части [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
