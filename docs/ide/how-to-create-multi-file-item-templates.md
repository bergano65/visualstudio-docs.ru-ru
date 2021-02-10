---
title: Создание многофайловых шаблонов элементов
description: Сведения о том, как создать шаблон элементов в Visual Studio, который включает несколько файлов.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: b375cf54dfe35928a35f991190c94b3d08685827
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875384"
---
# <a name="how-to-create-multi-file-item-templates"></a>Практическое руководство. Создание многофайловых шаблонов элементов

Шаблоны элемента могут указывать только один элемент, но иногда этот элемент состоит из нескольких файлов. Например, для шаблона элемента Windows Forms в Visual Basic требуется три следующих файла:

- файл, содержащий код для формы;

- файл, содержащий сведения конструктора для формы;

- файл, содержащий внедренные ресурсы для формы.

Многофайловым шаблонам элементов нужны параметры, чтобы при создании элемента использовались правильные расширения имен файлов. Если вы создаете многофайловый шаблон элемента с помощью мастера **экспорта шаблонов**, эти параметры создаются автоматически, а дальнейшая правка не требуется.

## <a name="use-the-export-template-wizard"></a>Использование мастера экспорта шаблонов

Многофайловый шаблон элемента создается аналогично однофайловому шаблону элемента. См. практическое руководство по [ Создание шаблонов элементов](../ide/how-to-create-item-templates.md). На странице **Выбор элементов для экспорта** мастера выберите файл, который содержит зависимые файлы (например, файл формы Windows Forms). Мастер автоматически включит в шаблон все зависимые файлы, например файлы ресурсов и конструктора.

## <a name="manually-create-a-multi-file-item-template"></a>Создание шаблона многофайлового элемента вручную

1. Создайте шаблон элемента так же, как если бы вы создавали однофайловый шаблон элемента вручную, но включите каждый файл, который составляет многофайловый элемент.

1. В *VSTEMPLATE*-файл XML-кода добавьте элемент `ProjectItem` для каждого отдельного файла и добавьте атрибут `TargetFileName` в этот элемент. Присвойте атрибуту `TargetFileName` значение *$входное_имя_файла$.расширение_файла*, где *расширение_файла* — это расширение файла, включаемого в шаблон. Пример:

    ```xml
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

     > [!NOTE]
     > Когда в проект добавляется элемент, производный от этого шаблона, имена файлов будут производными от имени, вводимого пользователем в диалоговом окне **Добавление нового элемента**.

1. Выберите файлы для включения в шаблон, щелкните выделение правой кнопкой мыши и выберите пункты **Отправить** > **Сжатая ZIP-папка**.

   Выбранные файлы будут сжаты в *ZIP*-файл.

1. Скопируйте *ZIP*-файл в расположение, где находится пользовательский шаблон элемента. По умолчанию это каталог *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates*. Дополнительные сведения см. в разделе [Практическое руководство. размещать и упорядочивать шаблоны](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Закройте Visual Studio, а затем откройте среду повторно.

1. Создайте новый проект или откройте существующий, а затем выберите **Проект** > **Добавить новый элемент** или нажмите клавиши **CTRL**+**SHIFT**+**A**.

   Многофайловый шаблон элемента появится в диалоговом окне **Добавление нового элемента**.

## <a name="example"></a>Пример

В приведенном ниже примере показан шаблон Windows Forms. Когда на основе этого шаблона создается элемент, имена трех созданных файлов будут соответствовать имени, введенному в диалоговом окне **Добавление нового элемента**.

```xml
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

- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Практическое руководство. замена параметров в шаблоне](../ide/how-to-substitute-parameters-in-a-template.md)
