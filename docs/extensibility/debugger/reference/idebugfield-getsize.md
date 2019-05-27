---
title: IDebugField::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6b2e48d83919de37bdc2c668d3e7f8e3e1d71a9
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212686"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Этот метод получает размер поля в байтах.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>Параметры
`pdwSize`\
[out] Возвращает размер.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Все поля имеют тип, и все типы имеют размер. Например поле с типом byte, имеет размер 1 байт.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)