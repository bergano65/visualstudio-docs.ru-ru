---
title: 'IDiaSymbol:: get_frontEndMinor | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b329cd69d010cba4e3667bde0d7b976389037bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740650"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
Извлекает дополнительный номер версии внешнего интерфейса.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает номер промежуточной части переднего плана.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Компилятор обычно состоит из двух основных элементов: внешнего интерфейса (средство синтаксического анализа), которое обрабатывает синтаксический анализ исходного кода в промежуточной форме и серверной части (генератор кода), который преобразует промежуточную форму в сборку. Нередко бывает, что внешний интерфейс имеет версию, отличную от версии серверной части.

 Номер версии внешнего интерфейса или серверной части состоит из трех частей: \<major >. > \<minor. \<build >, где \<major > — основной номер версии, \<minor > — дополнительный номер версии, а \<build > — номер сборки. Например, 13.10.3077.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)