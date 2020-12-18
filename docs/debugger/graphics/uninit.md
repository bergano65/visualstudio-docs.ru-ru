---
title: UnInit | Документация Майкрософт
description: Используйте метод Uninit() класса VsgDbg, чтобы завершить ведение журнала графики, закрыть файл журнала и освободить ресурсы, используемые для ведения этого журнала.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f79b39ced4f3285815412b9b231692868e5e00f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996062"
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