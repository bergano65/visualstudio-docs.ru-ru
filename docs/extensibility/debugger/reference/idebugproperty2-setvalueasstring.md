---
title: IDebugProperty2::SetValueAsString | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 310d2e3cd8c7f1caea4e245c7c591cd402afdaf4
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458876"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Задает значение свойства из данной строки.

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

 [in] Строка, содержащая значение, устанавливаемое значение.

 `nRadix`\

 [in] Основание системы счисления для использования в интерпретации все числовые данные. Это может быть 0, чтобы попытаться автоматически определить основание системы счисления.

 `dwTimeout`\

 [in] Указывает максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены другие возможные значения.

|Значение|Описание|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Не удалось преобразовать строку в значение свойства, или не удалось задать значение свойства.|
|`E_SETVALUE_VALUE_IS_READONLY`|Свойство доступно только для чтения.|

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)