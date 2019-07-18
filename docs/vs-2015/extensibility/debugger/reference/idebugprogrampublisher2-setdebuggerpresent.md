---
title: IDebugProgramPublisher2::SetDebuggerPresent | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 571da5e7baa720dc2e26fc629e2887cd0e3bdfa9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146294"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает издателя программы, что отладчик присутствует и работает.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```csharp  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fDebuggerPresent`  
 [in] Ненулевое значение (`TRUE`), если отладчик присутствует, ноль (`FALSE`) Если это не так.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Наличие или отсутствие отладчика отражается в данных, возвращаемых из [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод: значение, возвращаемое существует задается или отменить с предыдущего вызова `SetDebuggerPresent` метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
