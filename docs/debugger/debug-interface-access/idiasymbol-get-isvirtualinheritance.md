---
title: IDiaSymbol::get_isVirtualInheritance | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5d1630b46ca2203e9f935517e96b11856b273b9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631488"
---
# <a name="idiasymbolgetisvirtualinheritance"></a>IDiaSymbol::get_isVirtualInheritance
Указывает, является ли `this` указатель указывает на элемент данных с помощью виртуальное наследование.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isVirtualInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Указатель на `BOOL` , указывает ли `this` указатель указывает на элемент данных с помощью виртуальное наследование.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)