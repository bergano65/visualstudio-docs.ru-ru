---
title: IDiaSession::findFile | Документация Майкрософт
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
ms.openlocfilehash: 729b3c323ce2128b18af516ecbffb7b5157f0274
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642161"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Извлекает исходные файлы, компилируемого объекта и имя.

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

[in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий единице компиляции для использования в качестве контекста для поиска. Присвойте этому параметру значение `NULL` поиска исходных файлов во всех компилируемых объектах.

 `name`

[in] Задает имя исходного файла, который требуется получить. Присвойте этому параметру значение `NULL` для всех исходных файлов требуется получить.

 `option`

[in] Задает параметры сравнения, который применяется для поиска имени. Значения из [перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисления можно использовать отдельно или в сочетании.

 `ppResult`

[out] Возвращает [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) извлечь объект, содержащий список исходных файлов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>См. также раздел
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)