---
title: IDebugProgram2::Terminate | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5eb14280947ff93a4a0c2ab6d2cf025037fc06aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Завершает программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если это возможно программа будет завершен и выгружать из процесса; в противном случае модуль отладки (DE) будет выполнить необходимую очистку.  
  
 Этот метод или [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) метод вызывается в интегрированной среде разработки, обычно в ответ на прерывание всех отладки. Реализация этого метода в идеальном случае завершался программы внутри процесса. Если это невозможно, DE должно предотвратить выполнение этого процесса более программы (и выполнить необходимую очистку). Если `IDebugProcess2::Terminate` метод был вызван в интегрированной среде разработки, процесс будет завершен через некоторое время после `IDebugProgram2::Terminate` вызывается метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Завершение](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)