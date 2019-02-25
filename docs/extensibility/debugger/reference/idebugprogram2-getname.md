---
title: IDebugProgram2::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetName
helpviewer_keywords:
- IDebugProgram2::GetName
ms.assetid: a54cbf13-b3e3-4c9f-8b8d-13573232dfb0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9ec8a234e46fade2b58454d3f4cf8c4ff669564
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698291"
---
# <a name="idebugprogram2getname"></a>IDebugProgram2::GetName
Возвращает имя программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

#### <a name="parameters"></a>Параметры
 `pbstrName`

 [out] Возвращает имя программы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Имя возвращаемого этим методом всегда является понятным, отображаемое для пользователя имя, описывающее программы.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)