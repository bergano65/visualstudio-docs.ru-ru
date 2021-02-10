---
title: отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или выше| Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 01f8bf0b018ed5dd91cedcc221a037f3502815e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871498"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Ошибка: Отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или выше
Чтобы выполнить отладку смешанного собственного и управляемого кода в 64-разрядном процессе, необходимо использовать версию 4 платформы .NET Framework. Смешанный режим отладки для 64-разрядных процессов не поддерживается при использовании версий .NET Framework, предшествующих версии 4.

### <a name="to-correct-this-error"></a>Исправление ошибки

- Выполните одно из следующих действий.

  - Обновите .NET Framework до версии 4.

  - Постройте для отладки 32-разрядную версию приложения.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)