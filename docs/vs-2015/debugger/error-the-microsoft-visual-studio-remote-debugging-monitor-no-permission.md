---
title: 'Ошибка: Монитор удаленной отладки Microsoft Visual Studio на удаленном компьютере нет разрешения на подключение к этому компьютеру | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20accedd9591c777cad26aed30c05954dfabbdfc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811093"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Ошибка: монитор удаленной отладки Microsoft Visual Studio на удаленном компьютере не имеет разрешения на подключение к этому компьютеру
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данная ошибка возникает, если у пользователя, который пытается запустить монитор удаленной отладки Visual Studio (msvsmon), нет учетной записи на локальном компьютере.  
  
### <a name="to-fix-this-problem"></a>Для устранения этой проблемы:  
  
- Создайте на компьютере, с которого ведется отладка с помощью отладчика Visual Studio, учетную запись пользователя с таким же именем и паролем, что и в учетной записи пользователя, которая использовалась для запуска msvsmon на удаленном компьютере,  
  
   \- или -  
  
- Запустите msvsmon с правами пользователя, имеющего разрешение на удаленный вход на локальный компьютер. Это означает, что пользователь должен быть пользователем домена и администратором на компьютере msvsmon. Учетную запись для запуска msvsmon можно задать одним из двух способов:  
  
  - Щелкните правой кнопкой мыши значок msvsmon и выберите **запуска от имени** в контекстном меню  
  
    \- или -  
  
  - Запустите `runas.exe` в командной строке.  
  
## <a name="see-also"></a>См. также  
 [Удаленная отладка между доменами](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



