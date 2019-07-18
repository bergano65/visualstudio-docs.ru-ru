---
title: IDebugProgramProvider2::SetLocale | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::SetLocale
helpviewer_keywords:
- IDebugProgramProvider2::SetLocale
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 716ac7155c7e9885088a7197ac78f0834758dafe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324943"
---
# <a name="idebugprogramprovider2setlocale"></a>IDebugProgramProvider2::SetLocale
Устанавливает языковой стандарт для использования для любых ресурсов, зависящих от языкового стандарта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetLocale(
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Параметры
`wLangID`\
[in] Идентификатор языка для установки. Например 1033 для английского языка.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)