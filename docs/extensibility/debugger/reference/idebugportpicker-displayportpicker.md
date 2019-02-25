---
title: IDebugPortPicker::DisplayPortPicker | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e115c4e45784b2072bf626d90ebab0d980491e4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687358"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Отображает указанный диалоговое окно, которое позволяет пользователю выбрать порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

#### <a name="parameters"></a>Параметры
 `hwndParentDialog`

 [in] Дескриптор родительского диалогового окна.

 `pbstrPortId`

 [out] Строка идентификатора порта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращаемое значение, равное `S_FALSE` (или возвращаемое значение, равное `S_OK` с `BSTR` присвоено `NULL`) указывает, что пользователь нажал **отменить**.

## <a name="see-also"></a>См. также
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)