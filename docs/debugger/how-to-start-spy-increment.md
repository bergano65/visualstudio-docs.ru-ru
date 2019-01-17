---
title: Как выполнить Запуск Spy ++ | Документация Майкрософт
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f121bf823a65999b3c43f14f8e3e10d274a78c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896387"
---
# <a name="how-to-start-spy"></a>Как выполнить Запуск Spy++

Вы можете Запуск Spy ++ из Visual Studio или в командной строке.  
  
 При запуске Spy ++, если отображается сообщение, чтобы запросить разрешение на внесение изменений на компьютере, выберите **Да**.  
  
> [!NOTE]
>  Можно запустить только один экземпляр Spy ++. При попытке запустить второй экземпляр, то только что запущенного экземпляра получить фокус.

## <a name="prerequisites"></a>Предварительные требования

Spy ++ требуются следующие компоненты. Эти компоненты можно выбрать с помощью установщика Visual Studio, выбрав **отдельные компоненты** вкладку, а затем выберите следующие компоненты.

* Выберите Отладка и тестирование **средства профилирования C++**
* В разделе действия по разработке, выберите **основные возможности Visual Studio C++**

Если вы внесли изменения, следуйте инструкциям на экране для установки этих компонентов.
  
## <a name="start-spy-from-visual-studio"></a>Запуск Spy ++ из Visual Studio
  
На **средства** меню, выберите **Spy ++**.  
  
Поскольку Spy ++ работает независимо, после его запуска можно закрыть Visual Studio.  
  
> [!NOTE]
>  При записи сообщений в журнал с помощью Spy ++, он может привести к ОС, чтобы выполняться значительно медленнее.  
  
## <a name="start-spy-at-a-command-prompt"></a>Запуск Spy ++ в командной строке  
  
1.  В окне командной строки перейдите в папку, содержащую spyxx.exe. Как правило является путь к этой папке... \\ *Папка установки visual Studio*\Common7\Tools\\.  
  
2.  Введите **spyxx.exe**. 
  
## <a name="see-also"></a>См. также  
 [Использование Spy++](../debugger/using-spy-increment.md)   
 [Представления Spy++](../debugger/spy-increment-views.md)   
 [Справочник по Spy++](../debugger/spy-increment-reference.md)