---
title: IDebugCoreServer3::GetServerFriendlyName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f70e8301b6a44397d351345fe3cb8fe0c3d3426e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414034"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Возвращает понятное имя для сервера.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

#### <a name="parameters"></a>Параметры
 `pbstrName`

 [out] Возвращает понятное имя для сервера.

> [!NOTE]
> Вызывающий объект несет ответственность за освобождение строки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Для серверов запущен пользователем имя, возвращаемый этим методом является полное имя сервера. Для автоматического запуска серверов называется машины сервер работает.

 Для компьютера ориентированное имя, вызовите [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) метод.

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)