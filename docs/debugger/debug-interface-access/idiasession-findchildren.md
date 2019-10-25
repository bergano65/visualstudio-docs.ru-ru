---
title: 'IDiaSession:: Финдчилдрен | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca6778e5697c5f8821322c19d706d733d7f2b9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742292"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Извлекает все дочерние элементы указанного родительского идентификатора, соответствующие имени и типу символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

окне Объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий родительский элемент. Если этот родительский символ является функцией, модулем или блоком, то его лексические потомки возвращаются в `ppResult`. Если родительский символ является типом, возвращаются его дочерние элементы класса. Если этот параметр имеет значение `NULL`, для параметра `symtag` необходимо задать значение `SymTagExe` или `SymTagNull`, которое возвращает глобальную область (exe-файл).

 `symtag`

окне Указывает тег символа для извлекаемых дочерних элементов. Значения берутся из перечисления [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) . Задайте значение `SymTagNull`, чтобы получить все дочерние элементы.

 `name`

окне Указывает имя извлекаемых дочерних элементов. Задайте значение `NULL`, чтобы получить все дочерние элементы.

 `compareFlags`

окне Задает параметры сравнения, применяемые к соответствию имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.

 `ppResult`

заполняет Возвращает объект [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список полученных дочерних символов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
 В следующем примере показано, как найти локальные переменные `pFunc` функций, совпадающие с именем `szVarName`.

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>См. также
- [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)