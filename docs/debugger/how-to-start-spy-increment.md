---
title: Запуск Spy++ | Документация Майкрософт
description: Сведения о том, как запустить средство Spy++ из Visual Studio или из командной строки, если требуется выполнить отладку решения.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e8b1125534e52c810f97c91bd00ea53dfd3d6de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896629"
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
