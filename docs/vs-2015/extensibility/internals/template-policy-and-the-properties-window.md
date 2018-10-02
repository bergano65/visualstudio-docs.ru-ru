---
title: Шаблон политики и окне «Свойства» | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f8b2085818c539fe0e751a63562496363b43555
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572081"
---
# <a name="template-policy-and-the-properties-window"></a>Шаблон политики и окно свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [шаблон политики и окно свойств](https://docs.microsoft.com/visualstudio/extensibility/internals/template-policy-and-the-properties-window).  
  
Когда проект находится внутри шаблона корпоративного проекта, этот проект шаблона предприятия могут применять политику. Шаблон политики становится ограничивающий системе, где можно задать значения по умолчанию для свойств, скрыть свойства, добавить свойства и т. д.  
  
 С помощью шаблона политики для управления отображением данных **свойства** окно отличается от реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> обрабатывает свойства объекта на уровне компонента, хотя шаблона политики можно использовать для ограничения свойств объекта на уровне решения или проекта. Другими словами  
  
-   Реализуйте методы на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> для определения того, что должно отображаться в **свойства** окна для определенных объектов  
  
-   Использовать шаблон политики на уровне проекта и решения для определения того, что должно отображаться в **свойства** окно для ранее заданных объектов  
  
 С помощью шаблона политики выборочно ограничить определенные свойства в **свойства** окно при указанного типа элемента проекта, выбранного в **обозревателе решений** может быть важно для всех сотрудников команда разработчиков, работа над проектом. Например с помощью шаблона политики, можно настроить все сведения строки подключения в базе данных для разработчиков и убедитесь, строка подключения только для чтения. Таким образом вы можете указать простой способ убедиться, что каждый разработчик использует правильный путь для доступа к данным.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Расширение свойств](../../extensibility/internals/extending-properties.md)

