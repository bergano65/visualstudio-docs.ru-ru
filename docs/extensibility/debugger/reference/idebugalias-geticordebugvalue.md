---
title: IDebugAlias::GetICorDebugValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5068d687b80da5c75fdef305028c9b5c3d8e56ed
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615178"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Извлекает интерфейс управляемого кода, который представляет значение, связанное с данным псевдонимом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Параметры
`ppUnk`\
[out] `IUnknown` интерфейс, который представляет значение, связанное с данным псевдонимом. Этот интерфейс может запрашиваться для `ICorDebugValue` интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод применим только к значениям управляемых ( `ICorDebugValue` доступен интерфейс в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] и определен в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] пакета SDK в файле CorDebug.IDL).

## <a name="see-also"></a>См. также
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)