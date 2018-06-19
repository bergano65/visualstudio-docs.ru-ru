---
title: Интерфейс IDebugSessionProviderEx | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726934"
---
# <a name="idebugsessionproviderex-interface"></a>Интерфейс IDebugSessionProviderEx
Это основной интерфейс, предоставляемый отладчиком интегрированной среды разработки для отладки инициировал узла и языка. Он устанавливает сеанс отладки для выполняемого приложения. Этот интерфейс реализуется диспетчера отладки.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugSessionProviderEx` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Определяет, возможна ли отладка только в момент времени с указанным приложением.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Инициирует сеанс отладки с указанным приложением.|