---
title: IDebugProcess3::SetHostingProcessLanguage Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a16f2c39fa2d53ffc4d113666ef7630557e61861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723566"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Этот метод устанавливает язык, под которым будет размещаться процесс. Этот язык может быть использован движком отладки (DE) для загрузки соответствующего оценщика выражения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>Параметры
`guidLang`\
(в) `GUID` языка, который должен использовать DE. Укажите `GUID_NULL` (СЗ) `Guid.Empty` или (СЗ), чтобы DE использовал язык по умолчанию.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) можно использовать для получения текущей настройки языка.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
