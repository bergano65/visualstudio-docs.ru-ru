---
title: Практическое руководство. Создание шаблонов элементов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c120e94943d9e75c968ecf13fbdb1ec6d883eff2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "57867936"
---
# <a name="how-to-create-item-templates"></a>Практическое руководство. Создание шаблонов элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаги [первой процедуры](#to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box) этого раздела показывают, как создать шаблон элемента с помощью мастера **экспорта шаблона**. Если шаблон будет состоять из нескольких файлов, см. раздел [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md).  
  
 Мастер выполняет за вас большой объем работы по созданию базового шаблона, но во многих случаях необходимо вручную изменить VSTEMPLATE-файл после экспорта шаблона. Например, если элемент должен отображаться в диалоговом окне **Добавление нового элемента** для проекта приложения [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], необходимо выполнить ряд дополнительных действий. [Вторая процедура](#to-enable-the-item-template-to-be-used-in-a-store-project) этого раздела помогает выполнить данную задачу.  
 
 В некоторых случаях может потребоваться вручную создать шаблон элемента с нуля. В [третьей процедуре](#to-enable-templates-for-specific-project-sub-types) показано, как это сделать.  
  
 Сведения об элементах, которые можно использовать в VSTEMPLATE-файле, см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Чтобы добавить пользовательский шаблон элемента в диалоговое окно "Добавление нового элемента"  
  
1.  Создайте или откройте проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Добавьте элемент в проект и измените его по своему усмотрению.  
  
3.  Отредактируйте файл кода, чтобы указать, где должна быть выполнена замена параметра. Дополнительные сведения см. в разделе [Практическое руководство. Замена параметров в шаблоне](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  В меню **Файл** выберите команду **Экспорт шаблона**.  
  
5.  Щелкните **Шаблон элемента**, выберите проект, содержащий элемент, и нажмите кнопку **Далее**.  
  
6.  Выберите элемент, для которого требуется создать шаблон, и нажмите кнопку **Далее**.  
  
7.  Выберите ссылки на сборку, которые нужно включить в шаблон, и нажмите кнопку **Далее**.  
  
8.  Введите имя файла значка, изображение для предварительного просмотра, имя и описание шаблона и нажмите кнопку **Готово**.  
  
     Файлы для шаблона добавляются в ZIP-файл и копируются к тот каталог, который вы указываете в диалоговом окне. Расположением по умолчанию является папка **\Users\\<имя_пользователя\>\Documents\Visual Studio \<версия>\My Exported Templates\\**.  
  
    > [!WARNING]
    >  В более ранних версиях Visual Studio расположением по умолчанию является папка **\Users\\<имя_пользователя\>\Documents\Visual Studio \<версия>\Templates\ItemTemplates**.  
  
### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Включение шаблона элемента для использования в проекте Магазина  
  
1. Выполните шаги из предыдущей процедуры, чтобы экспортировать шаблон элемента.  
  
2. Извлеките VSTEMPLATE-файл из ZIP-файла, который был скопирован в папку \Users\\*имя_пользователя*\Documents\Visual Studio *версия*\Templates\ItemTemplates\ (или **My Exported Templates**).  
  
3. Откройте VSTEMPLATE-файл в Visual Studio.  
  
4. Для проекта C# Магазина Windows 8.1 в VSTEMPLATE-файле добавьте следующий XML-код между открывающим и закрывающим тегами `<TemplateData>`: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  
  
    Проект C++ магазина Windows 8.1 использует значение `WinRT-Native-6.3`. Для проектов Windows 10 и других типов проектов см. раздел [Элемент TemplateGroupID (шаблоны Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).  
  
    В следующем примере показано все содержимое VSTEMPLATE-файла после добавления строки XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`. Этот примере характерен для проектов C#. Можно изменить элементы <ProjectTpe> и \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> для указания других языков и типов проектов.  
  
   ```xml  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
     <TemplateData>  
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
       <Name>MyItemStoreTemplate</Name>  
       <Description>This is an example itemtemplate</Description>  
       <ProjectType>CSharp</ProjectType>  
       <SortOrder>10</SortOrder>  
       <Icon>__TemplateIcon.ico</Icon>  
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
     </TemplateData>  
     <TemplateContent>  
       <References />  
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    Сведения о других возможных значениях TemplateGroupID см. в разделе [Элемент TemplateGroupID (шаблоны Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)). Полный справочник по VSTEMPLATE-файлу см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
5. Сохраните VSTEMPLATE-файл в Visual Studio и закройте его.  
  
6. Скопируйте VSTEMPLATE-файл и снова вставьте его в ZIP-файл, расположенный в папке \Users\\*имя_пользователя*\Documents\Visual Studio *версия*\Templates\ItemTemplates\.  
  
    Если откроется диалоговое окно **Копирование файла**, выберите параметр **Копировать с заменой**.  
  
   Теперь можно добавить основанный на этом шаблоне элемент в проект [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] с помощью диалогового окна **Добавление нового элемента**.  
  
   Дополнительные сведения об именах параметров см. в разделе [Параметры шаблона](../ide/template-parameters.md).  
  
### <a name="to-enable-templates-for-specific-project-sub-types"></a>Включение шаблонов для конкретных подтипов проектов  
  
1. Среда разработки позволяет предоставлять элементы проекта из диалогового окна "Добавление элемента" для определенных типов проектов. Используйте эту процедуру, чтобы сделать пользовательские элементы доступными для проектов Windows, веб-сайтов, Office или баз данных.  
  
    Найдите в VSTEMPLATE-файле элемент ProjectType для шаблона элемента.  
  
    Добавьте элемент [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) сразу после элемента ProjectType.  
  
2. Задайте для элемента одно из следующих текстовых значений:  
  
   1. Windows  
  
   2. Office  
  
   3. База данных  
  
   4. Интернет  
  
      Например, `<ProjectSubType>Database</ProjectSubType>`.  
  
      В следующем примере показан шаблон элемента, доступный для проектов Office.  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
       <TemplateData>  
           <Name>Class</Name>  
           <Description>An empty class file</Description>  
           <Icon>Class.ico</Icon>  
           <ProjectType>CSharp</ProjectType>  
           <ProjectSubType>Office</ProjectSubType>  
           <DefaultName>Class.cs</DefaultName>  
       </TemplateData>  
       <TemplateContent>  
           <ProjectItem>Class1.cs</ProjectItem>  
       </TemplateContent>  
   </VSTemplate>  
  
   ```  
  
### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Создание шаблона элемента вручную без использования мастера экспорта шаблона  
  
1.  Создайте проект и его элемент.  
  
2.  Измените элемент проекта, пока он не будет готов к сохранению в качестве шаблона.  
  
3.  Отредактируйте файл кода соответствующим образом, чтобы указать, где должна быть выполнена замена параметра. Дополнительные сведения о замене параметров см. в разделе "Практическое руководство. Замена параметров в шаблоне".  
  
4.  Создайте XML-файл и сохраните его, используя расширение VSTEMPLATE, в том же каталоге, где находится новый шаблон элемента.  
  
5.  Создайте VSTEMPLATE-файл с кодом XML для предоставления метаданных шаблона элемента. Дополнительные сведения см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md) и в примере из предыдущего раздела.  
  
6.  Сохраните VSTEMPLATE-файл в и закройте его.  
  
7.  В проводнике Windows выберите файлы, которые нужно включить в шаблон, щелкните выбранное правой кнопкой мыши, выберите пункт "Отправить" и затем пункт "Сжатая ZIP-папка". Выбранные файлы будут сжаты в ZIP-файл.  
  
8.  Скопируйте ZIP-файл и вставьте его в расположение, где находится пользовательский шаблон элемента. В Visual Studio 2015 каталогом по умолчанию является \Users\\<имя_пользователя\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\. Дополнительные сведения см. в разделе "Практическое руководство. Размещение и упорядочение шаблонов проектов и элементов".  
  
## <a name="see-also"></a>См. также раздел  
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)