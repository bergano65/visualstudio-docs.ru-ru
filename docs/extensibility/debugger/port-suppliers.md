---
title: Порт поставщики | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf81cfeea10a0687e84982db595a5c7a9aab6074
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998226"
---
# <a name="port-suppliers"></a>Поставщики портов
В архитектуре отладчик *поставщика порта*:  
  
- Находится на сервере и предоставляет порты на запрос к этому серверу.  
  
- Можно добавлять и удалять порты из содержащую сервер.  
  
- Можно перечислить все порты, которые он предоставил к серверу.  
  
- Представленный [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс, который регистрируется с помощью Visual Studio через реестр. Этот интерфейс можно получить, вызвав [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет поставщика порта по умолчанию и порт по умолчанию. Если задан специальный порт должен быть реализован, поставщика пользовательского порта также необходимо реализовать для предоставления этих Настраиваемые порты.  
  
## <a name="see-also"></a>См. также  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Порты](../../extensibility/debugger/ports.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)