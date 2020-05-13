---
title: IDebugProperty3::CreateObjectID Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721174"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Создает уникальный идентификатор для этого свойства, чтобы убедиться, что он является уникальным среди всех других свойств.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается, когда диспетчер сеанса хочет убедиться, что это свойство однозначно идентифицировано среди всех других свойств. Двигатель отладки (DE) поддерживает этот метод, если свойства, с которой он занимается, уже однозначно идентифицированы. Если DE не поддерживает этот метод, он возвращается. `E_NOTIMPL`

 Любой уникальный `CreateObjectID` идентификатор, созданный с уничтожается при вызове метода [DestroyObjectID;](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) это также сигнализирует о конце необходимости однозначной идентификации этого свойства.

> [!NOTE]
> Существует нет метода для получения этого уникального идентификатора, так `CreateObjectID` что DE может делать все, что он хочет для уникальных идентификаторов, когда метод называется.

## <a name="see-also"></a>См. также
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
