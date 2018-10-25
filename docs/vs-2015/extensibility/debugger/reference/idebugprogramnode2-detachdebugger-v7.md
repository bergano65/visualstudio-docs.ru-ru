---
title: IDebugProgramNode2::DetachDebugger_V7 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 271a4053d90efd2d852e8b67ae8ad4d4353afa37
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822315"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ ИСПОЛЬЗУЙТЕ.  
  
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
 Реализация всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="remarks"></a>Примечания  
  
> [!WARNING]
>  Начиная с версии [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], этот метод больше не используется и всегда должны возвращать `E_NOTIMPL`.  
  
 Этот метод вызывается, когда отладчик неожиданно завершает работу. При вызове этого метода, DE следует возобновить программы, как если бы, если пользователь отсоединены от него. Следует отправлять дальнейшие события отладки. Программа должна находиться в состоянии там, где это присоединяемого элемента из другой экземпляр отладчика.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

