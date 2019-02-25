---
title: IDebugProgram2::GetENCUpdate | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 485684486c8d58dc9c7cbd3e679138360d02fdbb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708320"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Этот метод получает обновления изменить и продолжить "(ENC) для этой программы. Всегда возвращает пользовательского модуля отладки `E_NOTIMPL`.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

#### <a name="parameters"></a>Параметры
 `ppUpdate`

 [out] Возвращает внутренний интерфейс, который может использоваться для обновления этой программы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

> [!NOTE]
>  Всегда должны возвращать пользовательского модуля отладки `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)