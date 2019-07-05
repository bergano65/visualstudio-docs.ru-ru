---
title: IDebugDocumentContext2::Seek | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 413b1416adcd4b20231666e25f6a8044e632198b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325431"
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

## <a name="parameters"></a>Параметры
`nCount`\
[in] Число операторов или строк, продвинуться вперед, в зависимости от контекста документа.

`ppDocContext`\
[out] Возвращает новый [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объект с новой позиции.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)