---
title: Практическое руководство. Создание шаблонов многофайлового элемента | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda39459d0ddc0920dbb5b47157d90160ad3d166
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286797"
---
# <a name="how-to-create-multi-file-item-templates"></a>Практическое руководство. Создание многофайловых шаблонов элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаблоны элемента могут указывать только один элемент, но иногда этот элемент состоит из нескольких файлов. Например, шаблон элемента Windows Forms в Visual Basic требует три следующих файла:  
  
-   Файл VB, содержащий код для формы.  
  
-   Файл DESIGNER.VB, содержащий сведения конструктора для формы.  
  
-   Файл RESX, содержащий внедренные ресурсы для формы.  
  
 Шаблонам многофайлового элемента нужны параметры, чтобы обеспечить правильные расширения имен файлов при создании элемента в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Если вы создаете шаблон элемента с помощью мастера **экспорта шаблонов**, эти параметры создаются автоматически, а дальнейшая правка не требуется. Ниже описано, как использовать параметры, чтобы обеспечить создание правильных расширений имен файлов.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Создание шаблона многофайлового элемента вручную  
  
1.  Создайте шаблон элемента, как если бы вы создавали шаблон однофайлового элемента. Дополнительные сведения см. в статье [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md).  
  
2.  Добавьте атрибуты `TargetFileName` в каждый элемент `ProjectItem`. Присвойте атрибутам `TargetFileName` значения $входное_имя_файла$.*расширение_файла*, где *расширение_файла* — это расширение файла, включенное в шаблоне. Пример:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Когда в проект добавляется элемент, производный от этого шаблона, имена файлов будут основаны на имени, которое пользователь ввел в диалоговом окне **Добавление нового элемента**.  
  
3.  Выберите файлы, которые нужно включить в шаблон, щелкните выбранное правой кнопкой мыши, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**. Выбранные файлы будут сжаты в ZIP-файл.  
  
4.  Поместите ZIP-файл в расположение, где находится пользовательский шаблон элемента. По умолчанию это каталог \My Documents\Visual Studio *версия*\Templates\ItemTemplates\\. Дополнительные сведения см. в разделе [Практическое руководство. Размещение и упорядочение шаблонов и элементов](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Пример  
 Приведенный ниже пример показывает шаблон Windows Forms [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Когда на основе этого шаблона создается элемент, имена трех созданных файлов будут соответствовать имени, введенному в диалоговом окне **Добавление нового элемента**.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Практическое руководство. Замена параметров в шаблоне](../ide/how-to-substitute-parameters-in-a-template.md)



