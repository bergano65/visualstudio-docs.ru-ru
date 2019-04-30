---
title: IDebugSymbolProvider::GetAddressesFromContext | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7b28010f117b1bb6616250f1e188bd5acb38cda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915864"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Этот метод сопоставляет контекст документа в массив адресов отладки.

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

#### <a name="parameters"></a>Параметры
 `pDocContext`

 [in] Контекст документа.

 `fStatmentOnly`

 [in] Если значение равно TRUE, ограничивает адреса отладки для одной инструкции.

 `ppEnumBegAddresses`

 [out] Возвращает перечислитель для начала отладки адреса, связанные с этой инструкции или строке.

 `ppEnumEndAddresses`

 [out] Возвращает [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) перечислитель для конечного адреса отладки, связанные с этой инструкции или строке.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Контекст документа обычно обозначает диапазон строк источника. Этот метод содержит начальный и конечный адреса отладки связанных с такими строками. Некоторые языки допускают инструкций, которые охватывают несколько строк или строк, содержащих более одной инструкции. Этот метод предоставляет флаг для ограничения отладки адреса для одной инструкции.

 Вполне возможно, для одной инструкции иметь несколько адресов отладки, как и в случае шаблонов.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)