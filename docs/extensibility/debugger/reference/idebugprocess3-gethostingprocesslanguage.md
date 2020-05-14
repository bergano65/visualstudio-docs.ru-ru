---
title: IDebugProcess3::GetHostingProcessLanguage Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b27be0850755a1a2808c8c5c758a3ad59b41d7e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723615"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Этот метод `GUID` возвращает представляющий язык этого процесса, установленный вызовом [на SetHostingProcessLanguage.](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHostingProcessLanguage(
   GUID* pguidLang
);
```

```csharp
int GetHostingProcessLanguage(
   out Guid pguidLang
);
```

## <a name="parameters"></a>Параметры
`pguidLang`\
(ваут) Язык `GUID` этого процесса. `GUID_NULL`(СЗ) или `Guid.Empty` (СЗ) означает, что язык не установлен.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
