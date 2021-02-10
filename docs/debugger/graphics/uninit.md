---
title: UnInit | Документация Майкрософт
description: Используйте метод Uninit() класса VsgDbg, чтобы завершить ведение журнала графики, закрыть файл журнала и освободить ресурсы, используемые для ведения этого журнала.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905014"
---
# <a name="uninit"></a>UnInit
Финализирует файл журнала графики, закрывает его и освобождает все ресурсы, которые использовались во время активной записи данных графики приложением.

## <a name="syntax"></a>Синтаксис

```C++
void UnInit();
```

## <a name="remarks"></a>Примечания
 `UnInit` вызывается автоматически при уничтожении экземпляра класса `VsgDbg`. Если экземпляр `VsgDbg` не вел активной записи данных графики, ничего не происходит.

 После вызова `UnInit` для экземпляра `VsgDbg` новый файл журнала графики можно создать вызовом `Init` и финализировать вызовом `UnInit`. Это действие можно повторять сколько раз, сколько вы хотите использовать один и тот же экземпляр `VsgDbg` для создания нескольких независимых файлов журнала графики.

## <a name="see-also"></a>См. также
- [Init](init.md)