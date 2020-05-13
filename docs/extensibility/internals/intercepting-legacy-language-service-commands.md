---
title: Перехват команды службы устаревшей языковой службы (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707450"
---
# <a name="intercepting-legacy-language-service-commands"></a>Перехват команд языковой службы прежних версий
С [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]помощью , вы можете иметь языковой службы перехвата команд, что текстовое представление в противном случае обрабатывать. Это полезно для поведения, связанного с языком, которым не управляет текстовое представление. Вы можете перехватить эти команды, добавив один или несколько командных фильтров в текстовый вид из языковой службы.

## <a name="getting-and-routing-the-command"></a>Получение и routing команды
 Командный фильтр <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> — это объект, который отслеживает определенные последовательности символов или ключевые команды. Можно связать несколько командных фильтров с одним текстовым представлением. Каждое текстовое представление поддерживает цепочку командных фильтров. После создания нового командного фильтра вы добавляете фильтр в цепочку для соответствующего представления текста.

 Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> на добавить ваш командный фильтр в цепочку. При <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>вызове [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возвращается другой командный фильтр, на который можно передать команды, с которыми не обрабатывается ваш командный фильтр.

 У вас есть следующие варианты обработки команд:

- Ручка команды, а затем передать команду на следующий фильтр команды в цепочке.

- Обработка команды и не передайте команду следующему командованию.

- Не обрабатываете команду, а передайте команду следующему командованию.

- Игнорировать команду. Не обрабатываете его в текущем фильтре и не передайте его следующему фильтру.

  Для получения информации о том, с какими командами должна обрабатываться языковая служба, [см.](../../extensibility/internals/important-commands-for-language-service-filters.md)
