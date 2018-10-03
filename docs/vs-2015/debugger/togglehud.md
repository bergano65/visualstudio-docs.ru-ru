---
title: ToggleHUD | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b224fdbd4dfadc6af29a0491bba5a18089c260b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560603"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ToggleHUD](https://docs.microsoft.com/visualstudio/debugger/graphics/togglehud).  
  
Переключает диагностики графики *HUD* наложения (головной дисплей) или отключить.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Примечания  
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. В нем отображаются данные времени выполнения о приложении, а также о захвате данных графики и сообщения, которые добавляются путем вызова [AddMessage](../debugger/addmessage.md) функция-член.  
  
 Для переключения HUD, у вас нет активный захват графической информации — то есть он может включаться через экземпляр `VsgDbg` класса, но [Init](../debugger/init.md) не нужно сначала вызвать функцию-член.



