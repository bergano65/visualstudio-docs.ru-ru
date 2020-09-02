---
title: ToggleHUD | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144577"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Включает или выключает наложение *HUD* (головной дисплей) диагностики графики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Примечания  
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. На нем отображаются сведения о приложении во время выполнения и о захвате данных графики, а также сообщения, добавленные путем вызова функции-члена [AddMessage](../debugger/addmessage.md).  
  
 Чтобы включить HUD, необязательно вести активный захват данных графики: этот дисплей можно включить, используя экземпляр класса `VsgDbg`, но без предварительного вызова функции-члена [Init](../debugger/init.md).
