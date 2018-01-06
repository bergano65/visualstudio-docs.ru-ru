---
title: "ToggleHUD | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: baaa776a64d9b778c161ab7e65bb0f15e6c90099
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="togglehud"></a>ToggleHUD
Переключает диагностики графики *HUD* наложения (головной дисплей) или отключить.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Примечания  
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. В нем отображаются данные времени выполнения для приложений, а также о захвате данных графики и сообщений, которые добавляются путем вызова [AddMessage](addmessage.md) функции-члена.  
  
 Чтобы переключиться на HUD, не нужно активно захват графической информации — то есть, он может включаться через экземпляр `VsgDbg` класса, но [Init](init.md) функции-члена не должен вызываться сначала.