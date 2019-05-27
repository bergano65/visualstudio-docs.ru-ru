---
title: IDebugEngine3::SetJustMyCodeState | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fff1334c29ad4da5edb90c9a3b289582a8f616d8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212512"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Этот метод сообщает модулю отладки о JustMyCode сведения о состоянии.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Параметры
`fUpdate`\
[in] Ненулевое значение (`TRUE`) необходимо обновить сведения о текущем, нуль (`FALSE`) сбросить все данные (без учета, что-либо заданные ранее).

`dwModules`\
[in] Число структур сведения в `rgJMCSpec.`

`rgJMCSpec`\
[in] Массив [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) структур для использования.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 JustMyCode — это концепция Отладка только кода, к которой принадлежит пользователь и пропуск всех промежуточный код, например системного кода, даже если исходный код доступен для этого кода системы.

## <a name="see-also"></a>См. также
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)