---
title: "Порт поставщики | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 15
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
ms.openlocfilehash: bd603588a47f565f7f1d177c0740c3289afc8d7e
ms.lasthandoff: 02/22/2017

---
# <a name="port-suppliers"></a>Поставщикам портов
С точки зрения архитектуры отладчика **поставщика порта**:  
  
-   Содержится сервером и предоставляет порты на запрос к этому серверу.  
  
-   Можно добавлять и удалять порты на сервере, содержащем.  
  
-   Можно перечислить все порты, который поставляет на сервер.  
  
-   Представлена [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс, который зарегистрирован в реестре с помощью Visual Studio. Этот интерфейс можно получить, вызвав [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]предоставляет поставщика порта по умолчанию и порт по умолчанию. Если задан специальный порт должен быть реализован, поставщика настраиваемого порта также необходимо реализовать для предоставления этих пользовательских портов.  
  
## <a name="see-also"></a>См. также  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Порты](../../extensibility/debugger/ports.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
