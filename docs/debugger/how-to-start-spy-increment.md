---
title: 'Практическое: Запуск Spy ++ | Документация Майкрософт'
ms.custom: ''
ms.date: 11/12/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e2e5ffabbb560165bd19bb3d52b940a5cc9e858
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257173"
---
# <a name="how-to-start-spy"></a>Практическое руководство. Запуск Spy++
Вы можете Запуск Spy ++ из Visual Studio или в командной строке.  
  
 При запуске Spy ++, если отображается сообщение, чтобы запросить разрешение на внесение изменений на компьютере, выберите **Да**.  
  
> [!NOTE]
>  Можно запустить только один экземпляр Spy ++. При попытке запустить второй экземпляр, то только что запущенного экземпляра получить фокус.  
  
### <a name="start-spy-from-visual-studio"></a>Запуск Spy ++ из Visual Studio  
  
На **средства** меню, выберите **Spy ++**.  
  
Поскольку Spy ++ работает независимо, после его запуска можно закрыть Visual Studio.  
  
> [!NOTE]
>  При записи сообщений в журнал с помощью Spy ++, он может привести к ОС, чтобы выполняться значительно медленнее.  
  
### <a name="start-spy-at-a-command-prompt"></a>Запуск Spy ++ в командной строке  
  
1.  В окне командной строки перейдите в папку, содержащую spyxx.exe. Как правило является путь к этой папке... \\ *Папка установки visual Studio*\Common7\Tools\\.  
  
2.  Введите **spyxx.exe**. 
  
## <a name="see-also"></a>См. также  
 [Использование Spy ++](../debugger/using-spy-increment.md)   
 [Представления Spy ++](../debugger/spy-increment-views.md)   
 [Справочник по Spy++](../debugger/spy-increment-reference.md)