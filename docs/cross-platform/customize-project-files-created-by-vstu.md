---
title: Настройка файлов проекта, созданных в VSTU | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 7393d023b8c581b95d3ac39b8501ca9dbb30228d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="customize-project-files-created-by-vstu"></a>Настройка файлов проекта, созданных в VSTU
Набор средств Visual Studio для Unity обеспечивает обратный вызов в стиле Unity во время создания файла проекта. Выполните регистрацию с помощью события `VisualStudioIntegration.ProjectFileGeneration`, чтобы изменять файл проекта при каждом его повторном создании.

## <a name="demonstrates"></a>Демонстрации
 Как настраивать файлы проекта Visual Studio, создаваемые набором средств Visual Studio для Unity.

## <a name="example"></a>Пример

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
```

## <a name="see-also"></a>См. также
 [Share the Unity Log Callback with VSTU](../cross-platform/share-the-unity-log-callback-with-vstu.md) (Совместное использование обратного вызова журнала Unity с VSTU)
