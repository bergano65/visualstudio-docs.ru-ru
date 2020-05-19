---
title: UnInit | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734821"
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