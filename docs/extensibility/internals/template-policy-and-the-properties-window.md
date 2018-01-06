---
title: "Шаблон политики и окне «Свойства» | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 51735bf0f46e5a1ead6f989a8e75745ebc8e6e35
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="template-policy-and-the-properties-window"></a>Шаблон политики и окне «Свойства»
Когда проект содержится внутри шаблона корпоративного проекта, что корпоративный проект шаблона могут применять политику. Шаблон политики становится ограничивающий системы, для которого можно задать значения по умолчанию для свойств, скрытие свойств, Добавление свойств и так далее.  
  
 С помощью шаблона политики для управления отображением данных в **свойства** окно отличается от реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>обрабатывает свойства объекта на уровне компонентов, хотя шаблона политики можно использовать для ограничения свойств объекта на уровне решения или проекта. Другими словами  
  
-   Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> для определения того, что должно отображаться в **свойства** окна для конкретных объектов  
  
-   Использовать шаблон политики на уровне проекта и решения для определения того, что должно отображаться в **свойства** окна для ранее указанные объекты  
  
 С помощью шаблона политики выборочно ограничить конкретного свойства в **свойства** окно при элемента проекта указанного типа, выбранного в **обозревателе решений** может быть полезно для всех членов Работа над проектом команды разработчиков. Например с помощью шаблона политики, можно настроить всю информацию строки подключения в базу данных для разработчиков и сделать строку подключения только для чтения. Таким образом вы можете указать простой способ убедиться, что каждый разработчик использует правильный путь для доступа к данным.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Расширение свойств](../../extensibility/internals/extending-properties.md)