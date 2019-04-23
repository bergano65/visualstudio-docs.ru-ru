---
title: IDebugDocumentText2::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f9c46066393a930f6f30208940f0d18b3ed0883
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665580"
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

#### <a name="parameters"></a>Параметры
 `pcNumLines`

 [out] Возвращает количество строк текста.

 `pcNumChars`

 [out] Возвращает количество символов текста.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания

 [C++ только] Если определенное значение не требуется, передайте значение NULL для параметра.

 [C# только] Необходимо указать оба параметра.

## <a name="see-also"></a>См. также
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)