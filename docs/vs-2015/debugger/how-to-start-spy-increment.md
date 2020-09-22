---
title: Практическое руководство. Запуск Spy++ | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36555d9b00c9aff3f594ae2217afe8434bb41542
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843072"
---
# <a name="how-to-start-spy"></a>Практическое руководство. Запуск Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spy++ можно запустить из Visual Studio или командной строки.  
  
 Если при запуске Spy + + отображается сообщение, в котором запрашивается разрешение на внесение изменений в компьютер, нажмите кнопку **Да**.  
  
> [!NOTE]
> Вы можете запустить только один экземпляр Spy++. Если вы попытаетесь запустить другой экземпляр, он просто перейдет к текущему экземпляру, чтобы получить фокус.  
  
### <a name="to-start-spy-from-visual-studio"></a>Запуск Spy + + из Visual Studio  
  
- В меню **Сервис** выберите **Spy + +**.  
  
     Так как Spy + + выполняется независимо, после его запуска можно закрыть Visual Studio.  
  
    > [!NOTE]
    > Это, однако, может замедлить работу операционной системы при записи сообщений в журнал с помощью Spy++.  
  
### <a name="to-start-spy-at-a-command-prompt"></a>Запуск Spy + + из командной строки  
  
1. В окне командной строки измените каталоги на папку, содержащую spyxx.exe. Как правило, путь к этой папке —.. \\ *Папка установки Visual Studio*\Common7\Tools \\ .  
  
2. Введите **spyxx.exe** и нажмите клавишу ВВОД.  
  
## <a name="see-also"></a>См. также:  
 [Использование Spy + +](../debugger/using-spy-increment.md)   
 [Представления Spy + +](../debugger/spy-increment-views.md)   
 [Справочник по Spy++](../debugger/spy-increment-reference.md)
