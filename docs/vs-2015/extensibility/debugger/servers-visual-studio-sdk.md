---
title: Серверы (пакет SDK для Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e79e5e00bb4708359c19fd6a2ff95c7f31fd1179
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573390"
---
# <a name="servers-visual-studio-sdk"></a>Серверы (пакет SDK для Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [серверов (Visual Studio SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/servers-visual-studio-sdk).  
  
С точки зрения архитектуры отладчика **server**:  
  
-   Представляет контейнер портов и поставщикам портов и используется для передачи порты и поставщикам портов диспетчер отладки сеансов (SDM) и модули отладки.  
  
-   Можно перечислить его порты и поставщикам портов и идентификации по имени.  
  
-   Представленный [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс, который реализуется только с Visual Studio (один экземпляр сервера для каждого экземпляра работы Visual Studio).  
  
## <a name="see-also"></a>См. также  
 [Порты](../../extensibility/debugger/ports.md)   
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

