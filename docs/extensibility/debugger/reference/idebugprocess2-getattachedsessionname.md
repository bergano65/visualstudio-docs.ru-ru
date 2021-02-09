---
title: 'IDebugProcess2:: Жетаттачедсессионнаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4692fdbc08655553a829c0f44037221f2e8b410
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907857"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Возвращает имя сеанса, в котором выполняется отладка этого процесса. Интегрированная среда разработки может отображать эту информацию для пользователя, выполняющего отладку определенного процесса на определенном компьютере.

> [!NOTE]
> Этот метод является устаревшим, и его реализация всегда должна возвращать `E_NOTIMPL` .

## <a name="syntax"></a>Синтаксис

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Параметры
`pbstrSessionName`\

## <a name="return-value"></a>Возвращаемое значение
 Этот метод всегда должен возвращать `E_NOTIMPL` .

## <a name="see-also"></a>См. также раздел
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
