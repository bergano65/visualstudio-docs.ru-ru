---
title: Практическое руководство. Запуск Spy ++ | Документация Майкрософт
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442757"
---
# <a name="how-to-start-spy"></a>Практическое руководство. Запуск Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете Запуск Spy ++ из Visual Studio или в командной строке.  
  
 При запуске Spy ++, если отображается сообщение, чтобы запросить разрешения, чтобы вносить изменения на компьютере, нажмите кнопку **Да**.  
  
> [!NOTE]
> Можно запустить только один экземпляр Spy ++. При попытке запустить другой экземпляр, то только что запущенного экземпляра получить фокус.  
  
### <a name="to-start-spy-from-visual-studio"></a>Запуск Spy ++ из Visual Studio  
  
- На **средства** меню, щелкните **Spy ++**.  
  
     Поскольку Spy ++ работает. независимо друг от друга, после его запуска, можно закрыть Visual Studio.  
  
    > [!NOTE]
    > При записи сообщений в журнал с помощью Spy ++, он может привести к ОС, чтобы выполняться значительно медленнее.  
  
### <a name="to-start-spy-at-a-command-prompt"></a>Запуск Spy ++ в командной строке  
  
1. В окне командной строки перейдите в папку, содержащую spyxx.exe. Как правило путь этой папки является... \\ *Папка установки visual Studio*\Common7\Tools\\.  
  
2. Тип **spyxx.exe** и нажмите клавишу ВВОД.  
  
## <a name="see-also"></a>См. также  
 [Использование Spy++](../debugger/using-spy-increment.md)   
 [Представления Spy++](../debugger/spy-increment-views.md)   
 [Справочник по Spy++](../debugger/spy-increment-reference.md)
