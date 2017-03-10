---
title: "Настройка файлов проекта, созданных в VSTU | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 2
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9cac5f78264a03764071d2fa3716b30d717c45b6
ms.lasthandoff: 02/22/2017

---
# <a name="customize-project-files-created-by-vstu"></a>Настройка файлов проекта, созданных в VSTU
Набор средств Visual Studio для Unity обеспечивает обратный вызов в стиле Unity во время создания файла проекта. Выполните регистрацию с помощью события `VisualStudioIntegration.ProjectFileGeneration`, чтобы изменять файл проекта при каждом его повторном создании.  
  
## <a name="demonstrates"></a>Демонстрации  
 Как настраивать файлы проекта Visual Studio, создаваемые набором средств Visual Studio для Unity.  
  
## <a name="example"></a>Пример  
  
```c#  
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
