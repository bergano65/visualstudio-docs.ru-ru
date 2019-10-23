---
title: 'Ошибка: Отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или более поздней версии | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67b9d1c737e4490195b209abca824b2d6d51176c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737603"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Ошибка: отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или выше
Для отладки смешанного машинного и управляемого кода в 64-разрядном процессе необходимо иметь .NET Framework версии 4. Отладка в смешанном режиме для 64-разрядных процессов с .NET Framework версиями, предшествующими 4, не поддерживается.

### <a name="to-correct-this-error"></a>Исправление ошибки

- Выполните одно из следующих действий.

  - Обновите .NET Framework до версии 4.

  - Постройте для отладки 32-разрядную версию приложения.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)