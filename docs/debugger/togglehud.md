---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Переключает наложения *HUD* \(головной дисплей\) диагностики графики.  
  
## Синтаксис  
  
```cpp  
void ToggleHUD();  
```  
  
## Примечания  
 HUD диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики.  Он отображает сведения о приложении во время выполнения и о захвате данных графики и сообщения, которые добавляются путем вызова функции\-члена [AddMessage](../debugger/addmessage.md).  
  
 Чтобы переключить HUD, нет необходимости активно записывать данные графики: поддерживается переключение с помощью экземпляра класса `VsgDbg` без обязательного предварительного вызова функции\-члена [Init](../debugger/init.md).