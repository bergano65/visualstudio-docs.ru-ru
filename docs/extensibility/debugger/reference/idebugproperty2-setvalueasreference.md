---
title: IDebugProperty2::SetValueAsСправка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721252"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Устанавливает значение этого свойства к значению данной ссылки.

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
(в) Массив аргументов для передачи управляемому набору свойств кода. Если сеттер свойств не принимает аргументы или если этот объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) не `rgpArgs` относится к такому сеттеру свойств, должен быть нулевым значением. Этот параметр обычно является нулевая величина.

`dwArgCount`\
(в) Количество аргументов в `rgpArgs` массиве.

`pValue`\
(в) Ссылка в виде объекта [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) на значение, используемее для установки этого свойства.

`dwTimeout`\
(в) Сколько времени нужно, чтобы установить значение, в миллисекундах. Типичное значение `INFINITE`. Это влияет на время, которое может занять любая возможная оценка.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки, как правило, один из следующих:

|Error|Описание|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Установка значения из ссылки не поддерживается.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Значение не может быть установлено, так как это свойство относится к методу.|
|`E_SETVALUE_VALUE_IS_READONLY`|Значение только для чтения и не может быть установлено.|
|`E_NOTIMPL`|Метод не реализован.|

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
