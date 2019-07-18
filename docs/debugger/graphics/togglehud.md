---
title: ToggleHUD | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848474"
---
# <a name="togglehud"></a>ToggleHUD
Переключает диагностики графики *HUD* наложения (головной дисплей) или отключить.

## <a name="syntax"></a>Синтаксис

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Примечания
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. В нем отображаются данные времени выполнения о приложении, а также о захвате данных графики и сообщения, которые добавляются путем вызова [AddMessage](addmessage.md) функция-член.

 Для переключения HUD, у вас нет активный захват графической информации — то есть он может включаться через экземпляр `VsgDbg` класса, но [Init](init.md) не нужно сначала вызвать функцию-член.