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
ms.openlocfilehash: 00cc451aa9382011bdeb75f6414f13b5398ae89b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146334"
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