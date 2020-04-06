---
title: IDebugSymbolSearchEvent2:GetSymbolSearchInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718898"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Вызывается обработчиком событий для получения результатов процесса загрузки символа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Параметры
`pModule`\
(ваут) Объект IDebugModule3, представляющий модуль, для которого были загружены символы.

`pbstrDebugMessage`\
(в, вне) Возвращает строку, содержащую любые сообщения об ошибках из модуля. Если ошибки нет, то эта строка будет содержать имя модуля, но она никогда не бывает пустой.

> [!NOTE]
> (К) `pbstrDebugMessage` не `NULL` может быть и `SysFreeString`должен быть освобожден с .

`pdwModuleInfoFlags`\
(ваут) Комбинация флагов [из MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) перечисления, указывающие на то, были ли загружены какие-либо символы.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда обработчик получает событие [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) после попытки загрузить символы отладки для модуля, обработчик может вызвать thismethod, чтобы определить результаты этой нагрузки.

## <a name="see-also"></a>См. также
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
