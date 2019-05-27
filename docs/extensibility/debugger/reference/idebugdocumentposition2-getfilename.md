---
title: IDebugDocumentPosition2::GetFileName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0b1c2dbde9131d4dee25ff4d6535f8c835aafae
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211814"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Получает имя файла исходного файла, содержащий положение документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetFileName( 
   BSTR* pbstrFileName
);
```

```csharp
int GetFileName( 
   out string pbstrFileName
);
```

## <a name="parameters"></a>Параметры
`pbstrFileName`\
[out] Возвращает имя файла исходного файла.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Исходный файл не всегда возможно (исходный файл может не существует на диске, к примеру) имя файла.

## <a name="see-also"></a>См. также
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)