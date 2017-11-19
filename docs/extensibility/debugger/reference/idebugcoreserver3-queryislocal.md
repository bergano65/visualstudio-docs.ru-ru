---
title: "IDebugCoreServer3::QueryIsLocal | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::QueryIsLocal
helpviewer_keywords: IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc4a3e11e1dce483d368349cfb8d07d1c77e5f19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
Определяет, является локальным для вызывающего объекта сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` для указания локального сервера. Возвращает `S_FALSE` , если сервер работает на основе экземпляра msvsmon.exe, который обычно используется для удаленной отладки.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)