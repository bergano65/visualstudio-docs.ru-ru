---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Добавляет пользовательское сообщение в диагностические сведения графики *HUD* \(головной дисплей\).  
  
## Синтаксис  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### Параметры  
 `szMessage`  
 Сообщение, которое добавляется в HUD.  
  
## Примечания  
 HUD диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики.  Он отображает сведения о приложении во время выполнения и о захвате данных графики и сообщения, которые добавляются путем вызова этой функции.  
  
 Чтобы добавить сообщение в HUD, не обязательно активно записывать данные графики: сообщение можно добавить с помощью экземпляра класса `VsgDbg`, но без обязательного вызова функции\-члена [Init](../debugger/init.md).  Сообщения только отображаются в HUD, они не записываются в файл журнала графики.