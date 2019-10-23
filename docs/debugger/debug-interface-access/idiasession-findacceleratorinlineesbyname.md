---
title: IDiaSession::findAcceleratorInlineesByName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742314"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Возвращает перечисление символов для встроенных кадров, соответствующих указанному имени встроенной функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Параметры
 `name`

окне Имя встроенной функции для поиска.

 `option`

окне Параметры поиска по имени, используемые при поиске встраиваемых кадров, соответствующих `name`. Дополнительные сведения см. в разделе [перечисление намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

заполняет Указатель на указатель интерфейса `IDiaEnumSymbols`, который инициализируется с помощью результата.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Эта функция выполняет поиск встроенных функций только в функциях-заглушках ускорителя. Она не учитывает собственные C++ записи процедур.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)