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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ea45e3aa1f59353e0a395a61b0309144b413227
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223992"
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

## <a name="parameters"></a>Параметры
 `pAddress`\

 [in] Указанного адреса отладки.

 `fStatementOnly`\

 [in] Если значение равно TRUE, ограничивает адреса отладки для одной инструкции.

 `ppAddress`\

 [out] Возвращает следующий адрес отладки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает допустимый `HRESULT`, обычно S_OK.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)