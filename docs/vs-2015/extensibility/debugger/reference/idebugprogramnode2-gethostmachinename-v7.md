---
title: IDebugProgramNode2::GetHostMachineName_V7 | Документация Майкрософт
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
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2caab5eaa587274896015434abbda5d993569f22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559815"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgramNode2::GetHostMachineName_V7](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7).  
  
РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ ИСПОЛЬЗУЙТЕ.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrHostMachineName`  
 [out] Возвращает имя компьютера, в котором выполняется программа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="remarks"></a>Примечания  
  
> [!WARNING]
>  Начиная с версии [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], этот метод больше не используется и всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

