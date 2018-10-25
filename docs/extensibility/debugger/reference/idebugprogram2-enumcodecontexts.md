---
title: IDebugProgram2::EnumCodeContexts | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ddd3f6f3fe06b0a02a1df992561428aa04895748
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902520"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Извлекает список контексты для заданной позиции в файле исходного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```csharp  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocPos`  
 [in] [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) объект, представляющий абстрактный позиции в файле исходного кода, известные в интегрированную среду разработки.  
  
 `ppEnum`  
 [out] Возвращает [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) , содержащий список контексты кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет сеанса отладки manager (SDM) или интегрированной среде разработки, чтобы сопоставить позицию в файле источника в место кода. Более одного контекста кода возвращается в том случае, если источник создает несколько блоков кода (например, шаблоны C++).  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)