---
title: Порт поставщики | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f1ba09c1802bdeb1c6a402e95a6de408b277532
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099074"
---
# <a name="port-suppliers"></a>Поставщикам портов
С точки зрения архитектуры отладчик **поставщика порта**:  
  
-   Содержится на сервере и обеспечивает портов при запросе к этому серверу.  
  
-   Можно добавлять и удалять порты из содержащую сервер.  
  
-   Можно перечислить все порты, которые он предоставил на сервер.  
  
-   Представленный [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс, который зарегистрирован в Visual Studio через реестр. Этот интерфейс можно получить, вызвав [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет поставщик по умолчанию порт и порт по умолчанию. Если другой номер порта должен быть реализован, supplier нестандартного порта также необходимо реализовать для предоставления пользовательских порты.  
  
## <a name="see-also"></a>См. также  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Порты](../../extensibility/debugger/ports.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)