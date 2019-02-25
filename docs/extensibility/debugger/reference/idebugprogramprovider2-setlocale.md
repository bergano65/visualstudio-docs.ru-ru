---
title: IDebugProgramProvider2::SetLocale | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::SetLocale
helpviewer_keywords:
- IDebugProgramProvider2::SetLocale
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9a7d31f7ac442f4a6ff529ae46f1f7492665211
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722308"
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

#### <a name="parameters"></a>Параметры
 `wLangID`

 [in] Идентификатор языка для установки. Например 1033 для английского языка.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)