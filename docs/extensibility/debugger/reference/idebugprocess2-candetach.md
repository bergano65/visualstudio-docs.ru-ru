---
title: IDebugProcess2::CanDetach | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23a4ec112c33100a2eed8e4853f5a6280a741e12
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942144"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Определяет, если диспетчер отладки сеансов (SDM) можно отсоединить процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK.` возвращает `S_FALSE` Если отладчику не удается отсоединиться от процесса. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)