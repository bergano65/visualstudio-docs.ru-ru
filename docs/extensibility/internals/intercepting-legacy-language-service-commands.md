---
title: Перехват команд языковой службы прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bb888e83f10d887c15b9ebf9fd67acad28f8e4c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037763"
---
# <a name="intercepting-legacy-language-service-commands"></a>Перехват команд языковой службы прежних версий
С помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], у вас есть команд отсекаемый отрезок языковой службы, которые представление текста, в противном случае будет обрабатывать. Это полезно для конкретного языка поведение, которое не поддерживает управление представления текста. Может перехватывать эти команды, добавив один или несколько фильтров команд текстового представления из службы вашего языка.  
  
## <a name="getting-and-routing-the-command"></a>Получение и маршрутизация команды  
 Фильтр команд является <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект, который контролирует определенных последовательностей символов или клавиш. Фильтр более одной команды можно связать с одного текстового представления. Каждое представление текста поддерживает цепочке фильтров команд. После создания новый фильтр команды, вы добавляете фильтр в цепочку для представления соответствующий текст.  
  
 Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для добавления фильтра команд в цепочку. При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возвращает другой фильтр команд, к которому можно передать команды, которые не обрабатывают команды фильтра.  
  
 У вас есть следующие параметры для обработки команды:  
  
- Обработать команду, а затем передать команду к следующему фильтру команды в цепочке.  
  
- Обработать команду и не следует передавать команды к следующему фильтру команды.  
  
- Не обрабатывать команды, но передать команду к следующему фильтру команды.  
  
- Игнорируйте команды. Не обрабатывает его в текущий фильтр и не следует передавать его к следующему фильтру.  
  
  Сведения о командах, которые должен обрабатывать языковой службы, см. в разделе [важные команды для фильтров языковой службы](../../extensibility/internals/important-commands-for-language-service-filters.md).