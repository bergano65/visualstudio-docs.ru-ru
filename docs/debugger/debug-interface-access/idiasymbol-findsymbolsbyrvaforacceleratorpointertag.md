---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 673ca8137244fed933df0be3fa0221115951a9c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839001"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Учитывая соответствующее значение тега, этот метод возвращает перечисление символов, содержащихся в этой функции заглушки в указанный относительный виртуальный адрес.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Параметры
 `tagValue`

[in] Значение тега указатель, для которого находятся pointee символьные записи.

 `rva`

[in] RVA-адрес, используемый для фильтрации символы, которые соответствуют pointee переменную с указанным значением тега.

 `ppResult`

[out] Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с результатом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод следует вызывать только в `IDiaSymbol` интерфейс, который соответствует функции заглушки сочетаний клавиш.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)