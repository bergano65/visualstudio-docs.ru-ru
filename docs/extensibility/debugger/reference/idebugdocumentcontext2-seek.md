---
title: 'IDebugDocumentContext2:: Seek | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5be12a180368e668e944e0df822d5be6189f6ae0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946986"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Перемещает контекст документа на заданное количество инструкций или строк.

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
окне Число инструкций или строк, которое необходимо переместить вперед в зависимости от контекста документа.

`ppDocContext`\
заполняет Возвращает новый объект [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) с новой позицией.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
