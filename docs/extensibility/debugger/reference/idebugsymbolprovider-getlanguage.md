---
title: 'Идебугсимболпровидер:: отличный язык | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 876466d3617131815f6aa48b8b7dfb68b645ecb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719244"
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
окне Объект Address, представленный интерфейсом [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .

`pguidLanguage`\
заполняет Возвращает значение типа `GUID` , указывающее язык.

`pguidLanguageVendor`\
заполняет Возвращает значение типа `GUID` , указывающее поставщика языка.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Обработчик отладки вызывает этот метод для получения сведений, необходимых для выбора правильного средства оценки выражений.

## <a name="see-also"></a>См. также раздел
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
