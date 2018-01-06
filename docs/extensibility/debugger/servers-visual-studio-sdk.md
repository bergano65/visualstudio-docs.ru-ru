---
title: "Серверы (SDK для Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 404048e37f0a95ac1425250cfdcd098c4eb7f59d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="servers-visual-studio-sdk"></a>Серверы (SDK для Visual Studio)
С точки зрения архитектуры отладчик **сервера**:  
  
-   Является контейнером портов и поставщикам портов и используется для передачи порты и поставщикам портов диспетчера сеанса отладки (SDM) и отладки ядер.  
  
-   Можно перечислить его порты и поставщикам портов и идентифицироваться по имени.  
  
-   Представленный [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс, который реализуется только Visual Studio (один экземпляр сервера для каждого экземпляра Visual Studio запущена).  
  
## <a name="see-also"></a>См. также  
 [Порты](../../extensibility/debugger/ports.md)   
 [Поставщикам портов](../../extensibility/debugger/port-suppliers.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)