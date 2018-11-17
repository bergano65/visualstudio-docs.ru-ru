---
title: Шаблон политики и окне «Свойства» | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 695b65d65d03717dd2c2579584d61227ecf447cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767320"
---
# <a name="template-policy-and-the-properties-window"></a>Шаблон политики и окно свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Когда проект находится внутри шаблона корпоративного проекта, этот проект шаблона предприятия могут применять политику. Шаблон политики становится ограничивающий системе, где можно задать значения по умолчанию для свойств, скрыть свойства, добавить свойства и т. д.  
  
 С помощью шаблона политики для управления отображением данных **свойства** окно отличается от реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> обрабатывает свойства объекта на уровне компонента, хотя шаблона политики можно использовать для ограничения свойств объекта на уровне решения или проекта. Другими словами  
  
- Реализуйте методы на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> для определения того, что должно отображаться в **свойства** окна для определенных объектов  
  
- Использовать шаблон политики на уровне проекта и решения для определения того, что должно отображаться в **свойства** окно для ранее заданных объектов  
  
  С помощью шаблона политики выборочно ограничить определенные свойства в **свойства** окно при указанного типа элемента проекта, выбранного в **обозревателе решений** может быть важно для всех сотрудников команда разработчиков, работа над проектом. Например с помощью шаблона политики, можно настроить все сведения строки подключения в базе данных для разработчиков и убедитесь, строка подключения только для чтения. Таким образом вы можете указать простой способ убедиться, что каждый разработчик использует правильный путь для доступа к данным.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Расширение свойств](../../extensibility/internals/extending-properties.md)

