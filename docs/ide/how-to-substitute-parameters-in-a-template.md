---
title: Добавление параметров имен в шаблоны проектов и элементов
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3c8b6e0570567e8eb696fda61fe9db7bbd4a2f1b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283948"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Практическое руководство. Замена параметров в шаблоне

Параметры шаблонов позволяют заменять идентификаторы, такие как имена классов и пространства имен, при создании файла на основе шаблона. Параметры шаблона можно добавлять в существующие шаблоны или использовать для создания собственных шаблонов.

Параметры шаблона записываются в формате $*параметр*$. Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).

В следующем разделе показано, как изменить шаблон для замены имени пространства имен на безопасное имя проекта.

## <a name="example---namespace-name"></a>Пример — имя пространства имен

1. Вставьте параметр в один или несколько файлов кода в шаблоне. Пример:

    ```csharp
    namespace $safeprojectname$
    ```

1. В *VSTEMPLATE*-файле шаблона найдите элемент `ProjectItem`, содержащий этот файл.

1. Задайте для атрибута `ReplaceParameters` элемента `ProjectItem` значение `true`.

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>См. также раздел

- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
