---
title: PROGRAM_NODE_ARRAY | Документация Майкрософт
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
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a52cd55eba383854bf8140c8126d55175c112e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568909"
---
# <a name="programnodearray"></a>PROGRAM_NODE_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [PROGRAM_NODE_ARRAY](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/program-node-array).  
  
Содержит массив объектов, описывающих программы интерес.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagPROGRAM_NODE_ARRAY {  
   DWORD                dwCount;  
   IDebugProgramNode2** Members;  
} PROGRAM_NODE_ARRAY;  
```  
  
```csharp  
public struct tagPROGRAM_NODE_ARRAY {  
   public uint                 dwCount;  
   public IDebugProgramNode2[] Members;  
}  
```  
  
## <a name="members"></a>Участники  
 dwCount  
 Число объектов в `Members` массива.  
  
 Участники  
 Массив [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объектов, описывающих программы, в запросе.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является частью [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) структуру, которая в свою очередь заполняется с помощью вызова [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

