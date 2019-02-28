---
title: IDiaEnumInjectedSources::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aea793f33eb78ee1637d7f22eb46ba34514e0e8f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645047"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Извлекает указанное число источников, внедренного в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next ( 
   ULONG                celt,
   IDiaInjectedSource** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

[in] Число внедренного источников в перечислителе требуется получить.

 rgelt

[out] Возвращает массив [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) объекты, которые представляет нужный внедренного источники.

 pceltFetched

[out] Возвращает число внедренного источников в выбранных перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если существует больше нет внедренного источника. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)