---
title: 'Идебугмесодфиелд:: Жетглобалконтаинер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37e3b26a265fe651216e46fa299bdd827416b8ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727134"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Возвращает глобальный контейнер метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Параметры
`ppClass`\
заполняет Возвращает [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , представляющий модуль, в котором определен этот метод.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Возвращаемый объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) представляет весь модуль и является искусственным объектом, то есть сам модуль не имеет фактического класса, но может быть представлен `IDebugClassField` объектом, что позволяет перечислять и обнаруживать различные элементы модуля.

## <a name="see-also"></a>См. также раздел
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
