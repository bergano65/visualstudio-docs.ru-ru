---
title: 'IDiaEnumTables:: Clone | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 522ac4080331c869c32585dfed789378b1271542
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743797"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Clone ( 
   IDiaEnumTables** ppenum
);
```

#### <a name="parameters"></a>Параметры
 `ppenum`

заполняет Возвращает объект [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) , содержащий дубликат перечислителя. Таблицы не дублируются, только перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)