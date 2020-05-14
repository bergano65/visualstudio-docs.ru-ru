---
title: IDebugСимволпровайдер::GetAddressesFromPosition Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27767af36093e9424775074a55bafadac9a4480d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719402"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Этот метод отображает положение документа в массив адресов отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Параметры
`pDocPos`\
(в) Позиция документа.

`fStatmentOnly`\
(в) Если true, ограничивает адреса отладки одним утверждением.

`ppEnumBegAddresses`\
(ваут) Возвращает регистратор для исходных отладочных адресов, связанных с этой выпиской или строкой.

`ppEnumEndAddresses`\
(ваут) Возвращает enumerator [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) для адресов окончания отладки, связанных с этим утверждением или строкой.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Позиция документа обычно указывает диапазон исходных строк. Этот метод обеспечивает начальные и окончание отладки адреса, связанные с этими строками. Некоторые языки позволяют операторы, которые охватывают несколько строк, или строки, которые содержат более одного оператора. Этот метод предоставляет флаг для ограничения адресов отладки одним утверждением.

 Одно утверждение может иметь несколько адресов отладки, как в случае шаблонов.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
