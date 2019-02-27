---
title: IDiaSession::findAcceleratorInlineesByLinenum | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a2f23c42de99e0ea9a9d6c50e2d9aabed589d4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611156"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Возвращает перечисление символы для встроенных кадров, которые соответствуют указанным исходным расположением.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   IDiaSymbol*           parent,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 colnum,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

[in] `IDiaSymbol` , Соответствующий функции заглушки сочетаний клавиш, для которой необходимо выполнить поиск.

 `file`

[in] `IDiaSourceFile` Исходного расположения.

 `linenum`

[in] Номер строки исходного расположения.

 `colnum`

[in] Номер столбца исходного расположения.

 `ppResult`

[out] Указатель на `IDiaEnumLineNumbers` указатель интерфейса, который инициализируется с результатом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)