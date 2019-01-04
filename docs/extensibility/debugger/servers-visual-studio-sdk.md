---
title: Серверы (пакет SDK для Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 109c24935511f98e5eb3b5d83270960e5a0c6855
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905564"
---
# <a name="servers-visual-studio-sdk"></a>Серверы (пакет SDK для Visual Studio)
В архитектуре отладчик *server*:  
  
-   Представляет контейнер портов и поставщикам портов и передает порты и поставщикам портов диспетчер отладки сеансов (SDM) и отладчики.  
  
-   Можно перечислить его порты и поставщикам портов и идентификации по имени.  
  
-   Представленный [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс, который реализуется только с Visual Studio (один экземпляр сервера для каждого экземпляра работы Visual Studio).  
  
## <a name="see-also"></a>См. также  
 [Порты](../../extensibility/debugger/ports.md)   
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)