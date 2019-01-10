---
title: ToggleHUD | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4ee371f90636d98d5dd771cc508e58cd1d1a394
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907979"
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