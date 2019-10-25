---
title: 'IDiaSession:: Финдсимболсбирвафоракцелераторпоинтертаг | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1b24d24de35de30b24937a6cfbf59d12f69482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741993"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
При наличии соответствующего значения тега этот метод возвращает перечисление символов, содержащихся в указанной родительской функции-заглушке ускорителя, по указанному относительному виртуальному адресу.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

окне @No__t_0, соответствующий функции-заглушке ускорителя для поиска.

 `tagValue`

окне Значение тега указателя.

 `rva`

окне Относительный виртуальный адрес.

 `ppResult`

заполняет Указатель на указатель интерфейса `IDiaEnumSymbols`, который инициализируется с помощью результата.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Этот метод следует вызывать только в интерфейсе `IDiaSymbol`, соответствующем функции-заглушке ускорителя.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)