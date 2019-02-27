---
title: Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если вы не уверены, ниже сведения, не присоединяться к процессу | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f44c429dad42a0a46fe2c00f9b6a82dfcdb92b8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687254"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу
Это диалоговое окно с предупреждением появляется непосредственно перед присоединением к процессу, который содержит частично доверенный код или принадлежит недоверенному пользователю. Недоверенный процесс, содержащий вредоносный код, может нанести вред компьютеру, на котором выполняется отладка. Если имеется причина не доверять процессу, следует нажать кнопку **Отмена** для предотвращения отладки.

 Чтобы отключить это предупреждение при отладке надежного сценария, закройте Visual Studio и установите значение параметра реестра 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, а затем перезапустите Visual Studio. Завершив отладку данного сценария, вновь верните значение "0" и перезапустите Visual Studio.

 К числу "доверенных пользователей" относится ваша учетная запись, а также набор стандартных пользователей, которые обычно определены на компьютерах с установленной платформой .NET Framework, например: `aspnet`, `localsystem`, `networkservice` и `localservice`.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 Имя сборки, запрашиваемой для отладки

 Пользователь текущего пользователя

 Присоединение нажмите клавишу, чтобы продолжить отладку путем присоединения

 Не присоединение не присоединяться к процессу

## <a name="see-also"></a>См. также раздел
- [Подключение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Безопасность отладчика](../debugger/debugger-security.md)