---
title: Практическое руководство. Запуск Spy++ | Документация Майкрософт
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b659350adc39fd1088964976b8bcdef629bad44b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349008"
---
# <a name="how-to-start-spy"></a>Практическое руководство. Запуск Spy++

Spy++ можно запустить из Visual Studio или командной строки.

 Если при запуске Spy++ выводится сообщение с запросом разрешения на внесение изменений на компьютере, выберите **Да**.

> [!NOTE]
> Вы можете запустить только один экземпляр Spy++. Попытка запуска второго приведет лишь к перемещению фокуса на текущий запущенный экземпляр.

## <a name="prerequisites"></a>Предварительные требования

Для Spy++ требуются следующие компоненты. Вы можете выбрать эти компоненты в Visual Studio Installer на вкладке **Отдельные компоненты**.

* В разделе "Отладка и тестирование" выберите **Средства профилирования C++** .
* В разделе "Действия разработки" выберите **Основные компоненты C++** .

В случае внесения изменений следуйте инструкциям на экране, чтобы установить эти компоненты.

## <a name="start-spy-from-visual-studio"></a>Запуск Spy++ из Visual Studio

В меню **Сервис** выберите **Spy++** .

Так как программа Spy++ выполняется независимо, после ее запуска Visual Studio можно закрыть.

> [!NOTE]
> Это, однако, может замедлить работу операционной системы при записи сообщений в журнал с помощью Spy++.

## <a name="start-spy-at-a-command-prompt"></a>Запуск Spy++ из командной строки

1. В окне командной строки измените каталоги на папку, содержащую spyxx.exe. Как правило, к этой папке ведет следующий путь: ..\\*Visual Studio installation folder*\Common7\Tools\\.

2. Введите **spyxx.exe**.

## <a name="see-also"></a>См. также
- [Использование Spy++](../debugger/using-spy-increment.md)
- [Представления Spy++](../debugger/spy-increment-views.md)
- [Справочник по Spy++](../debugger/spy-increment-reference.md)
