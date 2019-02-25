---
title: IDebugDocumentContext2::Seek | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f001eb73e3c24ac1c9f15a4bd2c37c8d2cbe660e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709529"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Перемещает контекст документа, заданное число операторов или строк.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

#### <a name="parameters"></a>Параметры
 `nCount`

 [in] Число операторов или строк, продвинуться вперед, в зависимости от контекста документа.

 `ppDocContext`

 [out] Возвращает новый [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объект с новой позиции.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)