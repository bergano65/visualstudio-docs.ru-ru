---
title: "Кнопки окна свойств | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4cd83a8d8e72c18f8a6929e8985f7a8635a940d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-buttons"></a>Кнопки окна свойств
В зависимости от языка разработки и тип продукта, определенные кнопки отображаются по умолчанию на панели инструментов для **свойства** окна. Во всех случаях **по категориям**, **Alphabetized**, **свойства**, и **страницы свойств** отображаются кнопки. В Visual C# и Visual Basic **события** отображается кнопка. В некоторых проектах Visual C++ **сообщения VC ++** и **переопределяет VC** отображаются кнопки. Для других типов проектов могут отображаться дополнительные кнопки. Дополнительные сведения о кнопках в **свойства** окна, в разделе [окно свойств](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Реализация кнопки окна свойств  
 При нажатии кнопки **по категориям** кнопку вызовов Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> интерфейс для объекта, который имеет фокус, чтобы отсортировать ее свойства по категориям. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>Реализация `IDispatch` объекта, находящегося на **свойства** окна.  
  
 Имеется 11 предопределенное свойство категорий, которые имеют отрицательные значения. Можно определить пользовательские категории, однако рекомендуется назначить их положительные значения, чтобы отличать их от стандартных категорий.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Метод возвращает значение соответствующего свойства категории для заданного свойства. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Метод возвращает строку, содержащую имя категории. Достаточно для обеспечения поддержки пользовательской категории значений, так как Visual Studio будет стандартные категории значения свойств.  
  
 При нажатии кнопки **Alphabetized** кнопки свойства отображаются в алфавитном порядке по имени. Имена извлекаются путем `IDispatch` согласно локализованные алгоритма сортировки.  
  
 Когда **свойства** открыт, **свойства** кнопка автоматически отображается как выбранный. В других частях среды отображается та же кнопка, и можно щелкнуть его для отображения **свойства** окна.  
  
 **Страницы свойств** кнопка недоступна при `ISpecifyPropertyPages` не реализован для выбранного объекта. Отображение свойств зависящие от конфигурации, которые обычно связаны с решениями и проектами страницы свойств, но они могут быть также быть связаны с элементами проекта (например, в Visual C++).  
  
> [!NOTE]
>  Не удается добавить кнопки панели инструментов для **свойства** окна в неуправляемом коде. Чтобы добавить кнопки панели инструментов, необходимо создать управляемый объект, который является производным от <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)