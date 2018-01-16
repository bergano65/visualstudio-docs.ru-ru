---
title: "Добавление параметров имен в шаблоны проектов и элементов в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecdd277a36cb1c074653edb2af7f1882e6d25ede
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Практическое руководство. Замена параметров в шаблоне

Параметры шаблонов позволяют заменять идентификаторы, такие как имена классов и пространства имен, при создании файла на основе шаблона. Параметры шаблона можно добавлять в существующие шаблоны или использовать для создания собственных шаблонов.

Параметры шаблона записываются в формате $*параметр*$. Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).

В следующем разделе показано, как изменить шаблон для замены имени пространства имен на безопасное имя проекта.

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Использование параметра для замены имени пространства имен

1. Вставьте параметр в один или несколько файлов кода в шаблоне. Пример:

    ```csharp
    namespace $safeprojectname$
    ```

1. В VSTEMPLATE-файле шаблона найдите элемент `ProjectItem`, содержащий этот файл.

1. Задайте для атрибута `ReplaceParameters` элемента `ProjectItem` значение `true`.

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>См. также

[Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)  
[Параметры шаблона](../ide/template-parameters.md)  
[Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)