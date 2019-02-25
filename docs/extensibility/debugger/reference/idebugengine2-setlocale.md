---
title: IDebugEngine2::SetLocale | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28eb188ed5b388ac642399630b1891e165d6c9a2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703400"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Задает языковой стандарт модуля отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

#### <a name="parameters"></a>Параметры
 `wLangID`

 [in] Задает языковой стандарт. Например 1033 для английского языка.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается диспетчером сеанса отладки (SDM) для распространения параметрам национальной настройки интегрированной среды разработки, таким образом, чтобы строки, возвращаемые DE должным образом локализованы.

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)