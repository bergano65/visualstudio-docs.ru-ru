---
title: "How to: Start Spy++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++, starting"
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Start Spy++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spy\+\+ можно запустить либо из Visual Studio, либо из командной строки.  
  
 Если при запуске Spy\+\+ появляется сообщение, требующее разрешения на внесение изменений в систему, нажмите кнопку **Да**.  
  
> [!NOTE]
>  Возможен запуск только одной копии Spy\+\+.  При попытке запуска другого экземпляра на передний план будет выведен текущий экземпляр.  
  
### Запуск Spy\+\+ из Visual Studio  
  
-   В меню **Инструменты** выберите пункт **Spy\+\+**.  
  
     Поскольку Spy\+\+ работает независимо, после его запуска Visual Studio можно закрыть.  
  
    > [!NOTE]
    >  При записи сообщений в журнал с помощью Spy\+\+ производительность операционной системы может снизиться.  
  
### Запуск Spy\+\+ из командной строки  
  
1.  В окне командной строки перейдите папку, в которой находится файл spyxx.exe.  Обычно путь к этой папке:  \\*папка установки Visual Studio*\\Common7\\Tools\\.  
  
2.  Введите **spyxx.exe** и нажмите клавишу ВВОД.  
  
## См. также  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)