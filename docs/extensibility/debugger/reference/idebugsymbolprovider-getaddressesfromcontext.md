---
title: IDebugСимволпровайдер::GetAddressesFromContext Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719434"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Этот метод отображает контекст документа в массив адресов отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Параметры
`pDocContext`\
(в) Контекст документа.

`fStatmentOnly`\
(в) Если true, ограничивает адреса отладки одним утверждением.

`ppEnumBegAddresses`\
(ваут) Возвращает регистратор для исходных отладочных адресов, связанных с этой выпиской или строкой.

`ppEnumEndAddresses`\
(ваут) Возвращает enumerator [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) для адресов окончания отладки, связанных с этим утверждением или строкой.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Контекст документа обычно указывает диапазон исходных строк. Этот метод обеспечивает начальные и окончание отладки адреса, связанные с этими строками. Некоторые языки позволяют операторы, которые охватывают несколько строк, или строки, которые содержат более одного оператора. Этот метод предоставляет флаг для ограничения адресов отладки одним утверждением.

 Одно утверждение может иметь несколько адресов отладки, как в случае шаблонов.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
