---
title: Политика шаблона и окно "Свойства" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c67150c5a71a3d70df85669319795a405c60f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156026"
---
# <a name="template-policy-and-the-properties-window"></a>Шаблон политики и окно свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Если проект содержится в проекте корпоративного шаблона, этот проект шаблона предприятия может применить политику. Политика шаблона превращается в ограничивающую систему, которую можно использовать для задания значений по умолчанию для свойств, скрытия свойств, добавления свойств и т. д.  
  
 Использование политики шаблонов для управления отображением сведений в окне « **Свойства** » отличается от реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> обрабатывает свойства объекта на уровне компонента, а политика шаблона может использоваться для ограничения свойств объекта на уровне решения или проекта. Иными словами  
  
- Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> для определения того, что отображается в окне " **свойства** " для конкретных объектов.  
  
- Используйте политику шаблона на уровне решения и проекта, чтобы определить, что отображается в окне " **Свойства** " для ранее указанных объектов.  
  
  Использование политики шаблонов для выборочного ограничения определенных свойств в окне " **Свойства** " при выборе элемента проекта указанного типа в **Обозреватель решений** может быть полезным для всех членов группы разработчиков, работающих над проектом. Например, с помощью политики шаблонов можно настроить все данные строки подключения в базе данных для ваших разработчиков и сделать строку подключения доступной только для чтения. Таким образом, можно предоставить простой способ гарантировать, что каждый разработчик использует правильный путь для доступа к данным.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Расширение свойств](../../extensibility/internals/extending-properties.md)
