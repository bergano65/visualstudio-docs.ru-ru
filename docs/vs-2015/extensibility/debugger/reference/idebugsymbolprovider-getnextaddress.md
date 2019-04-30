---
title: IDebugSymbolProvider::GetNextAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1bf0798e0f49d9e7b2871c5601f966bc282b186
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421454"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Возвращает адрес отладки, следующий за адресом заданной отладочной в методе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

#### <a name="parameters"></a>Параметры
 `pAddress`

 [in] Указанного адреса отладки.

 `fStatementOnly`

 [in] Если значение равно TRUE, ограничивает адреса отладки для одной инструкции.

 `ppAddress`

 [out] Возвращает следующий адрес отладки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает допустимый `HRESULT`, обычно S_OK.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)