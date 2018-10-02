---
title: IDebugProgramNode2::DetachDebugger_V7 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: bf8948873818185285c3285bb8b2dbdaf4aac256
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570748"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgramNode2::DetachDebugger_V7](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7).  
  
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

