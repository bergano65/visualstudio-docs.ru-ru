---
title: IDebugProperty3::CreateObjectID | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1d2a66a5ed655c132526c5d73b6673a680c971
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339858"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Создает уникальный идентификатор для этого свойства, чтобы убедиться, что он является уникальным среди всех остальных свойств.

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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается, когда диспетчер отладки сеансов хочет убедиться, что это свойство однозначно идентифицируется среди всех остальных свойств. Модуль отладки (DE) поддерживает этот метод, если только свойства, которые он имеет дело с уже однозначно идентифицируются. Если DE не поддерживает этот метод, он возвращает `E_NOTIMPL`.

 Любой уникальный идентификатор, созданный с помощью `CreateObjectID` при уничтожении [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) вызывается метод; это также означает конец необходимость для уникальной идентификации этого свойства.

> [!NOTE]
> Нет метода для получения этот уникальный идентификатор, поэтому DE можно выполнять необходимые элементы для уникальных идентификаторов при `CreateObjectID` вызывается метод.

## <a name="see-also"></a>См. также
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)