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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e134b9b4adeb45693a9841a0a867a9c3630bf2aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835108"
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