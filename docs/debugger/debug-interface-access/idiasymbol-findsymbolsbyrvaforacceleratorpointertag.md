---
title: 'IDiaSymbol:: Финдсимболсбирвафоракцелераторпоинтертаг | Документация Майкрософт'
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
ms.openlocfilehash: f0d05946db816e6bd209e364e11d5091163941a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741155"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
При наличии соответствующего значения тега этот метод возвращает перечисление символов, содержащихся в этой функции-заглушке, по указанному относительному виртуальному адресу.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Параметры
 `tagValue`

окне Значение тега указателя, для которого обнаружены записи символов с точками.

 `rva`

окне RVA, используемый для фильтрации символов, соответствующих переменной-Point с указанным значением тега.

 `ppResult`

заполняет Указатель на указатель интерфейса `IDiaEnumSymbols`, который инициализируется с результатом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="remarks"></a>Заметки
 Этот метод следует вызывать только в интерфейсе `IDiaSymbol`, соответствующем функции-заглушке ускорителя.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)