---
title: ToggleHUD | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02b461ac8d80146bc86bf3636a367900fcdb8f39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786942"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Переключает диагностики графики *HUD* наложения (головной дисплей) или отключить.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Примечания  
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. В нем отображаются данные времени выполнения о приложении, а также о захвате данных графики и сообщения, которые добавляются путем вызова [AddMessage](../debugger/addmessage.md) функция-член.  
  
 Для переключения HUD, у вас нет активный захват графической информации — то есть он может включаться через экземпляр `VsgDbg` класса, но [Init](../debugger/init.md) не нужно сначала вызвать функцию-член.



