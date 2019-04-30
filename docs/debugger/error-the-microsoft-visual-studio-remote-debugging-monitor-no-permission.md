---
title: 'Ошибка: Монитор удаленной отладки Microsoft Visual Studio на удаленном компьютере не имеет разрешения на подключение к этому компьютеру'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac6e632927878988f8a3ff86d63fea080a45bd6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850446"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Ошибка: Монитор удаленной отладки Microsoft Visual Studio на удаленном компьютере не имеет разрешения на подключение к этому компьютеру

Данная ошибка возникает, если у пользователя, который пытается запустить монитор удаленной отладки Visual Studio (msvsmon), нет учетной записи на локальном компьютере.

## <a name="to-fix-this-problem"></a>Для устранения этой проблемы:

- Создайте на компьютере, с которого ведется отладка с помощью отладчика Visual Studio, учетную запись пользователя с таким же именем и паролем, что и в учетной записи пользователя, которая использовалась для запуска msvsmon на удаленном компьютере,

   \- или -

- Запустите msvsmon с правами пользователя, имеющего разрешение на удаленный вход на локальный компьютер. Это означает, что пользователь должен быть пользователем домена и администратором на компьютере msvsmon. Учетную запись для запуска msvsmon можно задать одним из двух способов:

  - Щелкните правой кнопкой мыши значок msvsmon и выберите **Запуск от имени** в контекстном меню

    \- или -

  - Запустите `runas.exe` в командной строке.

## <a name="see-also"></a>См. также

- [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)