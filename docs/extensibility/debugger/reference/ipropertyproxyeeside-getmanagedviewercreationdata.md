---
title: IPropertyProxyEEside::GetManagedViewerCreationData (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714964"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Извлекает информацию о зрителе для этого типа свойств, чтобы мгновенно увечить этого зрителя.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Параметры
`assemName`\
(ваут) Возвращает название сборки, вмещаемых этим объектом.

`assemBytes`\
(ваут) Возвращает объект [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) содержащий байты сборки этого объекта (это нулевая величина, если байты отсутствуют).

`assemPdb`\
(ваут) Возвращает `IEEDataStorage` объект, содержащий информацию о хранилище символов для этого объекта (это нулевое значение, если нет хранилища символов).

`className`\
(ваут) Возвращает имя класса, содержащее этот объект.

`alr`\
(ваут) Возвращает значение из [перечисления ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) с указанием местоположения сборки.

`replacementOk`\
(ваут) Возвращает ненулевой (`TRUE`), если значение этого объекта может быть изменено; ноль`FALSE`(), если объект читается только.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется визуализаторами типа для мгновенного мгновенного управляемого зрителя.

## <a name="see-also"></a>См. также
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
