---
title: "Развертывание пользовательского процессора директив | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7c7881c20412ab5ffc3f1c4486958f4b5ca68a1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-custom-directive-processor"></a>Развертывание пользовательского обработчика директив
Для использования пользовательского процессора директив в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] на любом компьютере необходимо зарегистрировать его одним из описанных в этом разделе способов.  
  
 Альтернативные методы таковы:  
  
-   [Расширение Visual Studio (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832). Предоставляет способ установки и удаления процессора директив на вашем и других компьютерах. Обычно можно упаковывать другие возможности в тот же VSIX.  
  
-   [VSPackage](../extensibility/internals/vspackages.md). Вы определяете VSPackage, содержащий помимо процессора директив и другие возможности; это удобный метод регистрации процессора директив.  
  
-   Определить раздел реестра. При использовании данного метода вы добавляете для процессора директив раздел реестра.  
  
 Эти методы необходимо использовать только в том случае, если требуется преобразовать текстовый шаблон в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Если используется в вашем собственном приложении, это пользовательское ведущее приложение отвечает за поиск процессора директив для каждой директивы.  
  
## <a name="deploying-a-directive-processor-in-a-vsix"></a>Развертывание процессора директив в VSIX  
 Можно добавить пользовательский процессор директив [расширения Visual Studio (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832).  
  
 Необходимо убедиться, что следующие два элемента содержатся в файле с расширением vsix:  
  
-   Сборка (dll), содержащая класс пользовательского процессора директив.  
  
-   Файл pkgdef, регистрирующий процессор директив. Корневое имя файла сборки должно совпадать с именем сборки. Например, файлы могут называться CDP.dll и CDP.pkgdef.  
  
 Чтобы просмотреть или изменить содержимое файла vsix, измените расширение его имени на zip и откройте этот файл. После изменения содержимого снова поменяйте расширение имени файла на vsix.  
  
 Файл vsix можно создать несколькими способами. Следующая процедура представляет один из них.  
  
#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Разработка пользовательского процессора директив в проекте VSIX  
  
1.  Создайте проект VSIX в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   В **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#**, затем разверните **расширяемости**. Нажмите кнопку **проект VSIX**.  
  
2.  В **source.extension.vsixmanifest**, тип содержимого и поддерживаемые выпуски.  
  
    1.  В VSIX редакторе манифестов на **активы** выберите **New** и задайте свойства нового элемента:  
  
         **Тип содержимого** = **VSPackage**  
  
         **Исходный проект** = \<*текущего проекта*>  
  
    2.  Нажмите кнопку **Выбранные выпуски** и отметьте типы установки, с которой процессор директив для использования.  
  
3.  Добавьте файл pkgdef и установит его свойства для включения в VSIX.  
  
    1.  Создайте текстовый файл и назовите его \< *assemblyName*> .pkgdef.  
  
         \<*assemblyName*> является обычно совпадает с именем проекта.  
  
    2.  Выберите его в обозревателе решений и задайте его свойства следующим образом:  
  
         **Действие построения** = **содержимого**  
  
         **Копировать в выходной каталог** = **всегда Копировать**  
  
         **Включить в VSIX** = **True**  
  
    3.  Задайте имя VSIX и убедитесь, что этот идентификатор уникален.  
  
4.  Добавьте в pkgdef-файл следующий текст:  
  
    ```  
    [$RootKey$\TextTemplating]  
    [$RootKey$\TextTemplating\DirectiveProcessors]  
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]  
    @="Custom Directive Processor description"  
    "Class"="NamespaceName.ClassName"  
    "CodeBase"="$PackageFolder$\AssemblyName.dll"  
    ```  
  
     Замените следующие имена собственными именами: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.  
  
5.  В проекте добавьте ссылки на следующее:  
  
    -   **Microsoft.VisualStudio.TextTemplating. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.VSHost. \*.0**  
  
6.  Добавьте в проект класс вашего пользовательского процессора директив.  
  
     Это открытый класс, который должен реализовывать тип <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> или <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
#### <a name="to-install-the-custom-directive-processor"></a>Установка пользовательского процессора директив  
  
1.  В Проводнике Windows (Проводнике в Windows 8) откройте каталог сборки (обычно это bin\Debug или bin\Release).  
  
2.  Если требуется установить процессор директив на другой компьютер, скопируйте vsix-файл на другой компьютер.  
  
3.  Дважды щелкните vsix-файл. Откроется окно установщика расширений [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Перезапустите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Теперь вы сможете запускать текстовые шаблоны, содержащие директивы со ссылками на ваш пользовательский процессор директив. Каждая директива имеет следующую форму:  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`  
  
#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Удаление или временное отключение пользовательского процессора директив  
  
1.  В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **средства** меню, нажмите кнопку **Диспетчер расширений**.  
  
2.  Выберите VSIX, содержащий процессор директив и нажмите кнопку **удаления** или **отключить**.  
  
### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Устранение неполадок процессора директив в VSIX  
 Если процессор директив не работает, этому могут быть следующие причины:  
  
-   Имя процессора, заданное в пользовательской директиве, должно соответствовать значению `CustomDirectiveProcessorName`, заданному в pkgdef-файле.  
  
-   Метод `IsDirectiveSupported` должен возвращать значение `true`, когда ему передается имя `CustomDirective`.  
  
-   Если вы не можете видеть расширение в диспетчере расширений, но системы не позволяют установить его, удалите это расширение из **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .  
  
-   Откройте vsix-файл и проверьте его содержимое. Чтобы его открыть, смените расширение имени файла на zip. Убедитесь, что он содержит файлы с расширениями dll, pkgdef и файл extension.vsixmanifest. Файл extension.vsixmanifest должен содержать соответствующий список в узле SupportedProducts, а также содержать узел VsPackage, расположенный в иерархии ниже узла Content.  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Развертывание процессора директив в VSPackage  
 Если процессор директив является частью VSPackage, который будет установлен в глобальный кэш сборок, можно сделать так, чтобы система сама сгенерировала pkgdef-файл.  
  
 Поместите в класс пакета следующий атрибут.  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
>  Этот атрибут следует поместить в класс пакета, не в класс процессора директив.  
  
 Файл pkgdef будет автоматически создан во время построения проекта. При установке VSPackage pkgdef-файл будет регистрировать процессор директив.  
  
 Убедитесь, что pkgdef-файл содержится в папке построения, которой обычно является bin\Debug или bin\Release. Если там нет этого файла, откройте CSPROJ-файл в текстовом редакторе и удалите следующий узел: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.  
  
 Дополнительные сведения см. в разделе [пакетов VSPackage](../extensibility/internals/vspackages.md).  
  
## <a name="setting-a-registry-key"></a>Создание раздела реестра  
 Данный способ установки пользовательского процессора директив рекомендуется использовать в последнюю очередь. Он не предусматривает удобного способа включения и отключения процессора директив и способа передачи процессора директив другим пользователям.  
  
> [!CAUTION]
>  Неправильное изменение реестра может привести к серьезному повреждению системы. Перед внесением изменений в реестр необходимо выполнить резервное копирование всех ценных данных на компьютере.  
  
#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Регистрация процессора директив путем создания раздела реестра  
  
1.  Запустите `regedit`.  
  
2.  В программе regedit перейдите следующему разделу:  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
     Если нужно установить процессор директив в экспериментальной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], после "11.0" вставьте "Exp".  
  
3.  Добавьте раздел реестра с именем, совпадающим с именем класса процессора директив.  
  
    -   В дереве реестра щелкните правой кнопкой мыши **DirectiveProcessors** узел, выберите пункт **New**, а затем нажмите кнопку **ключ**.  
  
4.  Добавьте в новый узел строковые значения для параметров Class и CodeBase либо Assembly согласно указаниям, приведенным в следующих таблицах.  
  
    1.  Щелкните правой кнопкой мыши созданный узел, выберите пункт **New**, а затем нажмите кнопку **строковое значение**.  
  
    2.  Отредактируйте имя значения.  
  
    3.  Дважды щелкните имя и отредактируйте данные.  
  
 Если пользовательский процессор директив не находится в глобальном кэше сборок, подраздел реестра должен выглядеть, как в следующей таблице:  
  
|name|Тип|Данные|  
|----------|----------|----------|  
|(Значение по умолчанию)|REG_SZ|(значение не задано)|  
|Класс|REG_SZ|**\<Имя пространства имен >. \<Имя класса >**|  
|CodeBase|REG_SZ|**\<Ваш путь >\\< ваше имя сборки\>**|  
  
 Если сборка находится в глобальном кэше сборок, подраздел реестра должен выглядеть, как в следующей таблице:  
  
|name|Тип|Данные|  
|----------|----------|----------|  
|(Значение по умолчанию)|REG_SZ|(значение не задано)|  
|Класс|REG_SZ|\<**На полное имя класса**>|  
|Assembly|REG_SZ|\<**Имя сборки в глобальном кэше СБОРОК**>|  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательских обработчиков директив для текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md)