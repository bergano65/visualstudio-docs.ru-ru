---
title: IDebugActivateDocumentEvent2::GetDocument | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocument
helpviewer_keywords:
- GetDocument method
- IDebugActivateDocumentEvent2::GetDocument method
ms.assetid: b3c32f1b-f3de-409d-920d-ba7b3fa84fcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ba06a44f24a6cd33c42b82bdf39aa4e4dfd799a
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615307"
---
# <a name="idebugactivatedocumentevent2getdocument"></a>IDebugActivateDocumentEvent2::GetDocument
Получает документ для активации.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocument ( 
   IDebugDocument2** ppDoc
);
```

```csharp
int GetDocument ( 
   out IDebugDocument2 ppDoc
);
```

## <a name="parameters"></a>Параметры
`ppDoc`\
[out] Возвращает [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) объект, представляющий документ, который активируется.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)