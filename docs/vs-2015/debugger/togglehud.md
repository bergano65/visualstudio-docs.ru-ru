---
title: ToggleHUD | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989230"
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
