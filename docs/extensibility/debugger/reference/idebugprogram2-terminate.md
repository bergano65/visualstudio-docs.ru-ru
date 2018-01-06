---
title: "IDebugProgram2::Terminate | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Terminate
helpviewer_keywords: IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fea9b99fc597a75e93392b14fe40a1be87072602
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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