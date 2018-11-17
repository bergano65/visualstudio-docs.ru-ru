---
title: Перехват команд языковой службы прежних версий | Документация Майкрософт
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
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41d89e2947cbd7bf1087f8dfa0ecffdd75033171
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752997"
---
# <a name="intercepting-legacy-language-service-commands"></a>Перехват команд языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

С помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], у вас есть команд отсекаемый отрезок языковой службы, которые представление текста, в противном случае будет обрабатывать. Это полезно для конкретного языка поведение, которое не поддерживает управление представления текста. Может перехватывать эти команды, добавив один или несколько фильтров команд текстового представления из службы вашего языка.  
  
## <a name="getting-and-routing-the-command"></a>Получение и маршрутизация команды  
 Фильтр команд является <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект, который контролирует определенных последовательностей символов или клавиш. Фильтр более одной команды можно связать с одного текстового представления. Каждое представление текста поддерживает цепочке фильтров команд. После создания новый фильтр команды, вы добавляете фильтр в цепочку для представления соответствующий текст.  
  
 Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для добавления фильтра команд в цепочку. При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] возвращает другой фильтр команд, к которому можно передать команды, которые не обрабатывают команды фильтра.  
  
 У вас есть следующие параметры для обработки команды:  
  
- Обработать команду, а затем передать команду к следующему фильтру команды в цепочке.  
  
- Обработать команду и не следует передавать команды к следующему фильтру команды.  
  
- Не обрабатывать команды, но передать команду к следующему фильтру команды.  
  
- Игнорируйте команды. Не обрабатывает его в текущий фильтр и не следует передавать его к следующему фильтру.  
  
  Сведения о командах, которые должен обрабатывать языковой службы, см. в разделе [важные команды для фильтров языковой службы](../../extensibility/internals/important-commands-for-language-service-filters.md).

