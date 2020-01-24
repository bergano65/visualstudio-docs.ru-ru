---
title: Руководство. Запуск Spy + + | Документация Майкрософт
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542624"
---
# <a name="how-to-start-spy"></a>Практическое руководство. Запуск Spy++

Spy + + можно запустить из Visual Studio или из командной строки.

 Если при запуске Spy + + выводится сообщение с запросом на внесение изменений в компьютер, выберите **Да**.

> [!NOTE]
> Можно запустить только один экземпляр Spy + +. Если вы попытаетесь запустить второй экземпляр, это приведет к тому, что текущий запущенный экземпляр получит фокус.

## <a name="prerequisites"></a>Prerequisites

Для Spy + + требуются следующие компоненты. Вы можете выбрать эти компоненты из Visual Studio Installer, выбрав вкладку **отдельные компоненты** , а затем выбрав следующие компоненты.

* В разделе Отладка и тестирование выберите  **C++ средства профилирования.**
* В разделе действия по разработке выберите  **C++ основные компоненты.**

Если вы внесли изменения, следуйте инструкциям на экране, чтобы установить эти компоненты.

## <a name="start-spy-from-visual-studio"></a>Запуск Spy + + из Visual Studio

В меню **Сервис** выберите **Spy + +** .

Так как Spy + + выполняется независимо, после запуска можно закрыть Visual Studio.

> [!NOTE]
> При записи сообщений в журнал с помощью Spy + + это может привести к более медленному выполнению операционной системы.

## <a name="start-spy-at-a-command-prompt"></a>Запуск Spy + + из командной строки

1. В окне командной строки измените каталоги на папку, содержащую spyxx. exe. Как правило, путь к этой папке —..\\*папку установки Visual Studio*\\\Common7\Tools.

2. Введите **spyxx. exe**.

## <a name="see-also"></a>См. также:
- [Использование Spy++](../debugger/using-spy-increment.md)
- [Представления Spy++](../debugger/spy-increment-views.md)
- [Справочник по Spy++](../debugger/spy-increment-reference.md)
