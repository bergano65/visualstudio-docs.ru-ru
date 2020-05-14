---
title: Совместное использование обратного вызова журнала Unity с VSTU | Документация Майкрософт
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: aa8a4a229102a6a9439ffb36582cd03e322a086b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815669"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Совместное использование обратного вызова журнала Unity с VSTU
Набор средств Visual Studio для Unity регистрирует обратный вызов журнала для потоковой передачи данных консоли Unity в Visual Studio. Если скрипты редактора также регистрируют обратный вызов журнала с Unity, обратный вызов VSTU может повлиять на работу вашего обратного вызова. Во избежание такой ситуации используйте событие `VisualStudioIntegration.LogCallback` для взаимодействия с VSTU.

## <a name="demonstrates"></a>Что демонстрирует
 Как совместно использовать обратный вызов журнала Unity, созданный средствами Visual Studio для Unity.

## <a name="example"></a>Пример

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>См. также раздел
 [Пример. Создание файла проекта](../cross-platform/customize-project-files-created-by-vstu.md)
