---
title: IDebugProgramNode2::GetEngineInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d49bbaf4ca4b4d85d198eeb51b2eb4d13508d39
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351157"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Возвращает имя и идентификатор для обработчика отладки (DE), выполнение программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Параметры
`pbstrEngine`\
[out] Возвращает имя DE, выполнение программы (C++-конкретных: это может быть указателем null, указывающее, что вызывающему объекту не требуется имя ядро).

`pguidEngine`\
[out] Возвращает глобальный уникальный идентификатор DE, выполнение программы (C++-конкретных: это может быть указателем null, указывающее, что вызывающий объект не заинтересован в идентификатор GUID модуля).

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)