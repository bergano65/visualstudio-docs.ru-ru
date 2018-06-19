---
title: Серверы (SDK для Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 2904641e8188abc6ef2382b2da272a9f96fd0f81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125498"
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