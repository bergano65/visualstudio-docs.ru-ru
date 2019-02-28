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
ms.openlocfilehash: fb3caa5574605864a0dd16b59b6f451530b8e631
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632242"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Возвращает перечисление символы для встроенных кадров, соответствующий имени функции задан встроенным.

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

[in] Имя функции встраиваемого метода для поиска.

 `option`

[in] Параметры поиска имени, используемый при поиске для встроенных кадров, соответствуют свойствам `name`. Дополнительные сведения см. в разделе [перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

[out] Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с результатом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Эта функция осуществляет поиск inlinees только внутри функции-заглушки сочетаний клавиш. Он игнорирует собственного C++ процедуру записи.

## <a name="see-also"></a>См. также раздел
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)