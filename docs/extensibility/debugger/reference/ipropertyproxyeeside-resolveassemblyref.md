---
title: IPropertyProxyEESide::ResolveAssemblyRef | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3294c19455b5ddf36ebecff52dab4908be84afab
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681417"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Определяет расположение ссылки указанной управляемой сборки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

#### <a name="parameters"></a>Параметры
 `assemName`

 [in] Имя сборки для решения.

 `assemBytes`

 [out] Возвращает [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий байты сборки, связанный со ссылкой.

 `assemPdb`

 [out] Возвращает `IEEDataStorage` объект, содержащий символ хранить данные, связанные с этой ссылкой.

 `assemLocation`

 [out] Возвращает путь данной ссылки.

 `alr`

 [out] Возвращает значение из [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) перечисление, указывающее расположение этой ссылки сборки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Обычно этот метод не реализован вычислителем пользовательское выражение.

## <a name="see-also"></a>См. также
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)