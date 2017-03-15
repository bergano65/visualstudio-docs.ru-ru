---
title: "Серверы (Visual Studio SDK) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2db4c9968cb585cab40c8b0138e610812483952d
ms.lasthandoff: 02/22/2017

---
# <a name="servers-visual-studio-sdk"></a>Серверы (SDK для Visual Studio)
С точки зрения архитектуры отладчика **сервера**:  
  
-   Представляет контейнер портов и поставщикам портов и используется для передачи порты и поставщикам портов диспетчера сеанса отладки (SDM) и отладки ядра.  
  
-   Могут идентифицироваться по имени и перечислить его порты и поставщикам портов.  
  
-   Представлена [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс, который реализуется только с помощью Visual Studio (один экземпляр сервера для каждого экземпляра Visual Studio запущена).  
  
## <a name="see-also"></a>См. также  
 [Порты](../../extensibility/debugger/ports.md)   
 [Поставщикам портов](../../extensibility/debugger/port-suppliers.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
