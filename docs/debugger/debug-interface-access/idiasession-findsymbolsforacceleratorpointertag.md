---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72510e9e82c1ec6983075880d4335dee8c0ad23c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839242"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Возвращает перечисление символов для переменной, которая соответствует указанным значением тега в родительском объекте функция заглушки сочетаний клавиш.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

[in] IDiaSymbol, соответствующую функцию заглушки сочетаний клавиш для поиска.

 `tagValue`

[in] Указатель на значение тега.

 `ppResult`

[out] Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с результатом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)