---
title: IDebugProperty2::SetValueAsString Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721236"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Устанавливает значение свойства из заданной строки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Параметры
`pszValue`\
(в) Строка, содержащая значение, подаваемый.

`nRadix`\
(в) Радикс, который будет использоваться при интерпретации любой численной информации. Это может быть 0, чтобы попытаться определить радикс автоматически.

`dwTimeout`\
(в) Определяет максимальное время, в миллисекундах, чтобы ждать, прежде чем вернуться из этого метода. Используйте, `INFINITE` чтобы ждать бесконечно.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки. В следующей таблице показаны другие возможные значения.

|Значение|Описание|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Строка не может быть преобразована в значение свойства, или значение свойства не может быть установлено.|
|`E_SETVALUE_VALUE_IS_READONLY`|свойство доступно только для чтения.|

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
