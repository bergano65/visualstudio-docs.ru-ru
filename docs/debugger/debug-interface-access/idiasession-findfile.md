---
title: 'IDiaSession:: Финдфиле | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9751127007b4e7823cf6d2ae35ed2fe80cb83b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742284"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Извлекает исходные файлы по компилируемого объекта и имени.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `pCompiland`

окне Объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий компилируемого объекта, который будет использоваться в качестве контекста для поиска. Присвойте этому параметру значение `NULL`, чтобы найти исходные файлы во всех компиляндов.

 `name`

окне Указывает имя исходного файла, который необходимо получить. Задайте для этого параметра значение `NULL` для всех извлекаемых исходных файлов.

 `option`

окне Задает параметры сравнения, применяемые к поиску имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.

 `ppResult`

заполняет Возвращает объект [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) , содержащий список извлекаемых исходных файлов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>См. также
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)