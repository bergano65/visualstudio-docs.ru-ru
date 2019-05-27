---
title: IDebugSymbolProvider::GetLanguage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86429e4ffe46fc182ea923f249bd5492dd433812
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207195"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Этот метод возвращает язык, который использовался для компиляции кода по адресу отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
[in] Адрес объекта, представленного [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.

`pguidLanguage`\
[out] Возвращает `GUID` , указывающее язык.

`pguidLanguageVendor`\
[out] Возвращает `GUID` , указывающий поставщика языка.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Отладчик вызывает этот метод, чтобы получить сведения, необходимые для выбора средство оценки выражений правильно.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)