---
title: Поставщики портов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153707"
---
# <a name="port-suppliers"></a>Поставщики портов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика **поставщик порта**:  
  
- Содержится в сервере и предоставляет порты по запросу к этому серверу.  
  
- Может добавлять и удалять порты на содержащем сервере.  
  
- Может перечислить все порты, предоставленные серверу.  
  
- Представляется интерфейсом [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , который зарегистрирован в Visual Studio в реестре. Этот интерфейс можно получить, вызвав [жетпортсупплиер](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предоставляет поставщик порта по умолчанию и порт по умолчанию. Если необходимо реализовать пользовательский порт, для предоставления этих настраиваемых портов также необходимо реализовать пользовательский порт.  
  
## <a name="see-also"></a>См. также:  
 [Серверах](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Порты](../../extensibility/debugger/ports.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
