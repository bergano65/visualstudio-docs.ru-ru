---
title: "Практическое руководство. Создание многофайловых шаблонов элементов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "шаблоны элементов, создание многофайловых шаблонов элементов"
  - "многофайловые шаблоны элементов"
  - "шаблоны Visual Studio, создание многофайловых шаблонов элементов"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Создание многофайловых шаблонов элементов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Шаблоны элементов могут определять только один элемент, но иногда элемент состоит из нескольких файлов.  Например, шаблон элемента Windows Forms в Visual Basic 3 требует следующих файлов:  
  
-   VB\-файла, содержащего код формы.  
  
-   DESIGNER.VB\-файла, содержащего сведения конструктора для формы.  
  
-   RESX\-файла, содержащего внедренные ресурсы для формы.  
  
 Многофайловые шаблоны элементов требуют использования параметров для обеспечения правильности используемых расширений имен файлов при создании элемента в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  При создании шаблона элемента с помощью мастера **Экспорт шаблона** эти параметры создаются автоматически и дальнейшее редактирование не требуется.  В следующей процедуре описаны способы использования параметров для обеспечения правильных создаваемых расширений имен файлов.  
  
### Чтобы вручную создать многофайловый шаблон элемента  
  
1.  Создайте шаблон элемента таким же образом, как и шаблон элемента из одного файла.  Дополнительные сведения см. в разделе [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md).  
  
2.  Добавьте атрибуты `TargetFileName` к каждому элементу `ProjectItem`.  Установите значение атрибутов `TargetFileName` на $fileinputname$.*расширение\_файла*, где *расширение\_файла* — это расширение имени файла, включенного в шаблон.  Примеры.  
  
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
  
     Когда элемент, производный от этого шаблона, добавляется в проект, имена файлов будут основываться на имени, введенном пользователем в диалоговом окне **Добавление нового элемента**.  
  
3.  Выберите файлы для включения в шаблон, щелкните их правой кнопкой мыши, выберите **Отправить**, затем щелкните **Сжатая ZIP\-папка**.  Выбранные файлы будут сжаты в ZIP\-файл.  
  
4.  Поместите ZIP\-файл в расположение с пользовательскими шаблонами элементов.  По умолчанию каталог \\Мои документы\\Visual Studio *номер версии*\\Templates\\ItemTemplates\\.  Дополнительные сведения см. в разделе [Практическое руководство. Размещение и упорядочение шаблонов и элементов](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## Пример  
 В следующем примере показан шаблон Windows Forms в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  При создании элемента, основанного на этом шаблоне, имена трех созданных файлов будут соответствовать имени, введенному в диалоговом окне **Добавление нового элемента**.  
  
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
  
## См. также  
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Практическое руководство. Замена параметров в шаблоне](../ide/how-to-substitute-parameters-in-a-template.md)