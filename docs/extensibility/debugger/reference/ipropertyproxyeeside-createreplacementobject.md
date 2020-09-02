---
title: 'Ипропертипроксеесиде:: функция createreplacementobject | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715039"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Создает копию объекта данных, относящегося к Вычислителю выражений (EE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Параметры
`dataIn`\
окне Объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , содержащий копируемые данные.

`dataOut`\
[out] Возвращает новый объект `IEEDataStorage`.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этому методу предоставляется объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , представляющий массив байтов. Этот объект входящих данных обычно не реализуется в EE. Однако объект, возвращаемый этим методом, всегда реализуется в EE, что позволяет `IEEDataStorage` классу ee реализовать интерфейс в любом нужном классе.

 Обратите внимание, что данные, передаваемые входящим `IEEDataStorage` объектом, должны быть одними и теми же данными в исходящем `IEEDataStorage` объекте.

## <a name="see-also"></a>См. также раздел
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
