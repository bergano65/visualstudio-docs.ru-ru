---
title: Добавление параметров имен в шаблоны проектов и элементов
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 93e553338478bcdead9e283323348b02ac73eaac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031764"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Как выполнить Замена параметров в шаблоне

Параметры шаблонов позволяют заменять идентификаторы, такие как имена классов и пространства имен, при создании файла на основе шаблона. Параметры шаблона можно добавлять в существующие шаблоны или использовать для создания собственных шаблонов.

Параметры шаблона записываются в формате $*параметр*$. Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).

В следующем разделе показано, как изменить шаблон для замены имени пространства имен на безопасное имя проекта.

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Использование параметра для замены имени пространства имен

1. Вставьте параметр в один или несколько файлов кода в шаблоне. Например:

    ```csharp
    namespace $safeprojectname$
    ```

1. В *VSTEMPLATE*-файле шаблона найдите элемент `ProjectItem`, содержащий этот файл.

1. Задайте для атрибута `ReplaceParameters` элемента `ProjectItem` значение `true`.

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>См. также

- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)