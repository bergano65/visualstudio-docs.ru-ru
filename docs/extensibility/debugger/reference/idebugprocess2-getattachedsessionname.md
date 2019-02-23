---
title: IDebugProcess2::GetAttachedSessionName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa932817c796249803558ad1eb877f620198b3e4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703553"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Получает имя сеанса, который выполняет отладку этого процесса. Интегрированная среда разработки для отображения этой информации для пользователя, который выполняет отладку определенного процесса на конкретном компьютере.

> [!NOTE]
>  Этот метод является устаревшим, и ее реализация должна всегда возвращать `E_NOTIMPL`.

## <a name="syntax"></a>Синтаксис

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

#### <a name="parameters"></a>Параметры
 `pbstrSessionName`

## <a name="return-value"></a>Возвращаемое значение
 Этот метод должен всегда возвращать `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)