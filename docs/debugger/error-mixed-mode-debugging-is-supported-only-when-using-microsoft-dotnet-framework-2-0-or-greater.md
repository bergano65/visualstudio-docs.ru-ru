---
title: 'Ошибка: Отладка в смешанном режиме поддерживается только при использовании Microsoft.NET Framework 2.0 или выше | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
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
ms.openlocfilehash: 2fb4d0dfaeb944700757c9ceec222dbd62dab9dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850679"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Ошибка: Смешанный режим отладки поддерживается только при использовании Microsoft.NET Framework 2.0 или выше
Чтобы выполнить отладку смешанного собственного и управляемого кода, необходимо наличие [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] версии 2.0, 3.0., 3.5 или 4. Отладка в смешанном режиме не поддерживается в более ранних версиях [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

### <a name="to-correct-this-error"></a>Исправление ошибки

- Обновите [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] до версии 2.0, 3.0, 3.5 или 4.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)