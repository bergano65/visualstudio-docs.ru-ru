---
title: "Совместное использование обратного вызова журнала Unity с VSTU | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-unity-tools
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: da0a8b98e358060cf11de87d9af2edf7e6b15f58
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Совместное использование обратного вызова журнала Unity с VSTU
Набор средств Visual Studio для Unity регистрирует обратный вызов журнала для потоковой передачи данных консоли Unity в Visual Studio. Если скрипты редактора также регистрируют обратный вызов журнала с Unity, обратный вызов VSTU может повлиять на работу вашего обратного вызова. Во избежание такой ситуации используйте событие `VisualStudioIntegration.LogCallback` для взаимодействия с VSTU.

## <a name="demonstrates"></a>Демонстрации
 Как совместно использовать обратный вызов журнала Unity, созданный средствами Visual Studio для Unity.

## <a name="example"></a>Пример

```csharp
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
```

## <a name="see-also"></a>См. также
 [Настройка файлов проекта, созданных в VSTU](../cross-platform/customize-project-files-created-by-vstu.md)
