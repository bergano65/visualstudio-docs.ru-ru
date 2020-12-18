---
title: ToggleHUD | Документация Майкрософт
description: Используйте метод ToggleHUD() класса VsgDbg, чтобы включить отображение головного дисплея диагностики графики (HUD) при выполнении приложения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60bee5a89be0fc1503595a36cfc48a692711d40a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996075"
---
# <a name="togglehud"></a>ToggleHUD
Включает или выключает наложение *HUD* (головной дисплей) диагностики графики.

## <a name="syntax"></a>Синтаксис

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Примечания
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. На нем отображаются сведения о приложении во время выполнения и о захвате данных графики, а также сообщения, добавленные путем вызова функции-члена [AddMessage](addmessage.md).

 Чтобы включить HUD, необязательно вести активный захват данных графики: этот дисплей можно включить, используя экземпляр класса `VsgDbg`, но без предварительного вызова функции-члена [Init](init.md).