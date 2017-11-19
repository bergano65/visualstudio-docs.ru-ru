---
title: "Перехват команды службы языка для прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73524ce47dfea2d30e44e51e97bf584a95a86482
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="intercepting-legacy-language-service-commands"></a>Перехват команды службы языка для прежних версий
С [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], у вас есть команды отсекаемый отрезок языковой службы, которые представления текста, в противном случае будет обрабатываться. Это полезно для конкретного языка поведение, которое не поддерживает управление представления текста. Эти команды можно перехватить, добавив один или несколько фильтров команды для представления текста из службы языка.  
  
## <a name="getting-and-routing-the-command"></a>Получение и маршрутизация команды  
 Команда фильтр <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект, который отслеживает определенные последовательности символов или клавиш. Более одного фильтра команду можно связать с одно текстовое представление. Каждое текстовое представление поддерживает фильтры цепочке управления. После создания нового фильтра команды добавления фильтра в цепочке в соответствующее текстовое представление.  
  
 Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для добавления фильтра команды в цепочку. При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возвращает другой фильтр команды, к которому можно передать команды, команда фильтра не может обрабатывать.  
  
 Имеются следующие параметры для обработки команды.  
  
-   Обработать команду, а затем передайте команду на фильтр следующей команды в цепочке.  
  
-   Обработать команду, а не передавать команды на следующей фильтрации команд.  
  
-   Не обрабатывать команды, но передать команду на следующей фильтрации команд.  
  
-   Игнорируйте команды. Не обрабатывает его в текущий фильтр и не следует передавать его на следующий фильтр.  
  
 Сведения о какие команды обработки службы языка см. [важные команды для фильтров службы языка](../../extensibility/internals/important-commands-for-language-service-filters.md).