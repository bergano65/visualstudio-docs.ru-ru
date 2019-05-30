---
title: IDebugDocumentText2::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f382b1d27a83e4493431ac8e6cca3d6aef9dd72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337377"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Получает размер текста в этой позиции в документе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Параметры
`pcNumLines`\
[out] Возвращает количество строк текста.

`pcNumChars`\
[out] Возвращает количество символов текста.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания

 [C++ только] Если определенное значение не требуется, передайте значение NULL для параметра.

 [C# только] Необходимо указать оба параметра.

## <a name="see-also"></a>См. также
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)