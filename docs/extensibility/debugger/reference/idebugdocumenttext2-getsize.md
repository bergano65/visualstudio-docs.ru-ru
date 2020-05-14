---
title: IDebugДокументТекст2::GetSize Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731589"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Извлекает размер текста в этой позиции в документе.

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
(ваут) Возвращает количество строк текста.

`pcNumChars`\
(ваут) Возвращает количество символов текста.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания

 (только си) Если определенное значение не желательно, передайте NULL для параметра.

 (Только для C) Оба параметра должны быть указаны.

## <a name="see-also"></a>См. также
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
