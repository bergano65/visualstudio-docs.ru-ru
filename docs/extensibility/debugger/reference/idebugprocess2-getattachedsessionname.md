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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b70fd48adacdbbf936c6997fc373ad4a8d7e696b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724064"
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
