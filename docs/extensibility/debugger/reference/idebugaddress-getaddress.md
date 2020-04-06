---
title: IDebugАдрес::GetАдрес Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736605"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Возвращает структуру, описывающую объект и его местоположение в пределах его области или контейнера.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
(в, вне) Структура [DEBUG_ADDRESS,](../../../extensibility/debugger/reference/debug-address.md) заполненная этим методом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) передается этому методу, который затем заполняет его соответствующей информацией. Способ интерпретации этой информации зависит от вида возвращенной информации и самого обработчика символов. Более подробную информацию можно узнать [DEBUG_ADDRESS.](../../../extensibility/debugger/reference/debug-address.md)

## <a name="see-also"></a>См. также
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
