---
title: IDiaSymbol::get_backEndMajor | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc62c81a1a57b9e9921b6df658d05e8a0a541da0
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64830387"
---
# <a name="idiasymbolgetbackendmajor"></a>IDiaSymbol::get_backEndMajor
Извлекает серверной части основной номер версии компилятора.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_backEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает номер основной версии серверной части. См. заметки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Компилятор обычно состоит из двух основных элементов: переднего плана (средство синтаксического анализа), который обрабатывает синтаксического анализа исходного кода в промежуточный форму, и серверной частью (генератор кода), который преобразует промежуточную форму в сборку. Нередко для внешнего интерфейса до имеют версию, отличную от серверной части.

 Интерфейс или номер версии серверной части состоит из трех частей: \<основных >.\< дополнительный номер >. \<сборки >, где \<основных > — номер основной версии \<незначительные > — это дополнительный номер версии, и \<сборки > — номер сборки. Например, 13.10.3077.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)