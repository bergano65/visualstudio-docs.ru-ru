---
title: Практическое руководство. Замена параметров в шаблоне | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670664"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Практическое руководство. Замена параметров в шаблоне
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете заменить параметры шаблона, такие как имена классов и пространства имен, при создании файла на основе шаблона. Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).

## <a name="procedure"></a>Процедура
 Параметры в файлах шаблона можно заменить при создании проекта на основе этого шаблона. Здесь описывается, как создать шаблон, который заменяет имя пространства имен на безопасное имя проекта при создании нового проекта с помощью шаблона.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Использование параметра для замены имени пространства имен именем проекта

1. Вставьте параметр в один или несколько файлов кода в шаблоне. Пример:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Параметры шаблона записываются в формате $*параметр*$.

2. В VSTEMPLATE-файле шаблона найдите элемент `ProjectItem`, содержащий этот файл.

3. Задайте для атрибута `ReplaceParameters` элемента `ProjectItem` значение `true`. Пример:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>См. также раздел
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md) . [Параметры шаблона](../ide/template-parameters.md) [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md) [элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
