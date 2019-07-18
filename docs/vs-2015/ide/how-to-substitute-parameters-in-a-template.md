---
title: Практическое руководство. Замена параметров в шаблоне | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c0a710bc3ad504c6654528db33b9a6698f4f7ae
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435160"
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
  
## <a name="see-also"></a>См. также  
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
