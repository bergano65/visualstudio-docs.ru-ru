---
title: 'IDebugProperty2:: Сетвалуеасреференце | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2ed6cbf32d807734714f25453e33fe8bdd7fac0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961798"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Присваивает этому свойству значение, равное заданной ссылке.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Параметры
`rgpArgs`\
окне Массив аргументов, передаваемый методу задания свойств управляемого кода. Если метод задания свойств не принимает аргументы или этот объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) не ссылается на такой метод задания свойства, то `rgpArgs` должен иметь значение null. Обычно этот параметр имеет значение null.

`dwArgCount`\
окне Число аргументов в `rgpArgs` массиве.

`pValue`\
окне Ссылка в виде объекта [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) на значение, используемое для задания этого свойства.

`dwTimeout`\
окне Время, затрачиваемое на задание значения (в миллисекундах). Типичное значение — `INFINITE` . Это влияет на время, в течение которого может выполняться любая возможная оценка.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки, обычно один из следующих:

|Ошибка|Описание|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Установка значения из ссылки не поддерживается.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Значение не может быть задано, так как это свойство ссылается на метод.|
|`E_SETVALUE_VALUE_IS_READONLY`|Значение доступно только для чтения и не может быть задано.|
|`E_NOTIMPL`|Метод не реализован.|

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
