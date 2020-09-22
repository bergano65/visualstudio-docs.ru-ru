---
title: IDebugProgramNode2::D etachDebugger_V7 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842789"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Не рекомендуется. НЕ ИСПОЛЬЗУЙТЕ.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация всегда должна возвращать `E_NOTIMPL` .  
  
## <a name="remarks"></a>Remarks  
  
> [!WARNING]
> Начиная с [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , этот метод больше не используется и всегда должен возвращать `E_NOTIMPL` .  
  
 Этот метод вызывается при внезапном завершении работы отладчика. При вызове этого метода программа DE должна возобновить работу программы так, как будто пользователь отсоединяется от нее. Больше не нужно отправлять события отладки. Программа должна находиться в состоянии, в котором она может быть присоединена из другого экземпляра отладчика.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
