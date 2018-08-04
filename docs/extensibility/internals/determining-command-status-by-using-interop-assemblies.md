---
title: Определение состояния команды с помощью сборок взаимодействия | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 005779b71e6c4fe748cadda787d5acef41d4e173
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498133"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Определение состояния команды с помощью сборок взаимодействия
VSPackage должен хранить список команд, которые он может обрабатывать состояние. Среду не удается определить, когда обрабатывается в VSPackage команды становится включен или отключен. Он отвечает за вашего VSPackage, чтобы сообщить среде о состояниях команды, например, состояние общие команды, такие как **Вырезать**, **копирования**, и **вставить**.  
  
## <a name="status-notification-sources"></a>Состояние уведомления источников  
 Среде получает сведения о командах через пакеты VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, который является частью реализации VSPackage из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Среда вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> методе VSPackage в двух случаях:  
  
-   Когда пользователь открывает главного меню или контекстного меню (щелкнув), в среде выполняется <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод на все команды меню, чтобы определять их состояние.  
  
-   Когда VSPackage запрашивает, что среде обновить текущий пользовательский интерфейс (UI). Это обновление происходит в том, как команды, видимых в настоящее время для пользователя, такие как **Вырезать**, **копирования**, и **вставить** группирования на стандартной панели инструментов, становятся включенных и отключенных в ответ на действия контекста и пользователем.  
  
 Так как оболочка размещает несколько пакетов VSPackage, оболочки бы неприемлемо привести к снижению производительности если требовалось опроса каждого пакета VSPackage, чтобы определить состояние команды. Вместо этого VSPackage активно должно уведомить среду, при изменении его пользовательского интерфейса во время изменения. Дополнительные сведения о уведомление об обновлении, см. в разделе [обновить пользовательский интерфейс](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Сбой состояния уведомления  
 Письменно вашего VSPackage среду об изменении состояния команды можно поместить пользовательский Интерфейс в несогласованном состоянии. Помните, что любой из команд меню и контекстного меню можно разместить на панели инструментов пользователем. Таким образом обновление пользовательского интерфейса, только в том случае, когда откроется меню или команду контекстного меню будет недостаточно.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Реализация](../../extensibility/internals/command-implementation.md)