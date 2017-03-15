---
title: "Пошаговое руководство. Использование MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
caps.latest.revision: 32
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: ecfd08a410983561f3c1e761eb25302b6d9281c4
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-using-msbuild"></a>Пошаговое руководство. Использование MSBuild
MSBuild является платформой сборки для корпорации Майкрософт и Visual Studio. Это практическое руководство содержит вводную информацию о стандартных блоках MSBuild и описывает способы записи и отладки проектов MSBuild, а также управления ими. Здесь рассматриваются следующие вопросы:  
  
-   создание файла проекта и работа с ним;  
  
-   использование свойств сборки;  
  
-   использование элементов сборки.  
  
 MSBuild можно запустить в Visual Studio или из командного окна. В этом пошаговом руководстве вы создадите файл проекта MSBuild с помощью Visual Studio. Вы отредактируете файл проекта в Visual Studio и с помощью окна командной строки выполните сборку проекта и просмотрите результаты.  
  
## <a name="creating-an-msbuild-project"></a>Создание проекта MSBuild  
 Система проектов Visual Studio основана на MSBuild. Это упрощает создание файла проекта с помощью Visual Studio. В этом разделе создается файл проекта Visual C#. Вместо него можно выбрать создание файла проекта Visual Basic. В контексте данного пошагового руководства различия между двумя файлами проекта незначительны.  
  
#### <a name="to-create-a-project-file"></a>Создание файла проекта  
  
1.  Запустите Visual Studio.  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В диалоговом окне **Создание проекта** выберите тип проекта Visual C#, а затем — шаблон **Приложение Windows Forms**. В поле **Имя** введите `BuildApp`. Введите **расположение** решения, например `D:\`. Примите параметры по умолчанию **Создать каталог для решения** (выбран), **Добавить в систему управления версиями** (не выбран) и **Имя решения** (`BuildApp`).  
  
     Нажмите кнопку **ОК**, чтобы создать файл проекта.  
  
## <a name="examining-the-project-file"></a>Анализ файла проекта  
 В предыдущем разделе вы использовали Visual Studio для создания файла проекта Visual C#. Файл проекта представлен в **обозревателе решений** узлом проекта с именем BuildApp. Чтобы проанализировать файл проекта, можно использовать редактор кода Visual Studio.  
  
#### <a name="to-examine-the-project-file"></a>Анализ файла проекта  
  
1.  В **обозревателе решений** выберите узел проекта BuildApp.  
  
2.  В браузере **Свойства** обратите внимание, что свойство **Файл проекта** имеет значение BuildApp.csproj. В именах всех файлов проектов указан суффикс proj. Если вы создали проект Visual Basic, файлу проекта будет задано имя BuildApp.vbproj.  
  
3.  Щелкните правой кнопкой мыши узел проекта, а затем выберите **Выгрузить проект**.  
  
4.  Еще раз щелкните правой кнопкой мыши узел проекта, а затем выберите **Изменить BuildApp.csproj**.  
  
     Файл проекта откроется в редакторе кода.  
  
## <a name="targets-and-tasks"></a>Целевые объекты и задачи  
 Файлы проекта представляют собой файлы в формате XML с корневым узлом [Проект](../msbuild/project-element-msbuild.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Project ToolsVersion="12.0" DefaultTargets="Build"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Необходимо указать пространство имен xmlns в элементе "Проект".  
  
 Создание приложения выполняется с помощью элементов [Целевой объект](../msbuild/target-element-msbuild.md) и [Задача](../msbuild/task-element-msbuild.md).  
  
-   Задача — это наименьшая единица работы или, другими словами, атом сборки. Задачи являются независимыми исполняемыми компонентами, которые могут иметь входные и выходные данные. Сейчас в проекте отсутствуют определенные задачи или задачи, на которые существуют ссылки. Процедура добавления задач в файл проекта описывается в следующих разделах. Дополнительные сведения см. в статье о [задачах](../msbuild/msbuild-tasks.md).  
  
-   Целевой объект представляет собой именованную последовательность задач. В конце файла проекта существует два целевых объекта, которые в настоящее время заключены в комментарии HTML: BeforeBuild и AfterBuild.  
  
    ```xml  
    <Target Name="BeforeBuild">  
    </Target>  
    <Target Name="AfterBuild">  
    </Target>  
    ```  
  
     Дополнительные сведения см. в статье о [целевых объектах](../msbuild/msbuild-targets.md).  
  
 Узел "Проект" имеет необязательный атрибут DefaultTargets, выбирающий целевой объект по умолчанию для сборки, в этом случае — Build.  
  
```xml  
<Project ToolsVersion="12.0" DefaultTargets="Build" ...  
```  
  
 Целевой объект Build не определен в файле проекта. Он импортируется из файла Microsoft.CSharp.targets с помощью элемента [Import](../msbuild/import-element-msbuild.md).  
  
```xml  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Импортированные файлы вставляются в файл проекта везде, где на них указывает ссылка.  
  
 MSBuild отслеживает целевые объекты сборки и гарантирует, что каждый целевой объект будет построен не более одного раза.  
  
## <a name="adding-a-target-and-a-task"></a>Добавление целевого объекта и задачи  
 Добавьте целевой объект в файл проекта. Добавьте задачу в целевой объект, который выводит сообщение.  
  
#### <a name="to-add-a-target-and-a-task"></a>Добавление целевого объекта и задачи  
  
1.  Добавьте следующие строки в файл проекта сразу после оператора Import:  
  
    ```xml  
    <Target Name="HelloWorld">  
    </Target>  
    ```  
  
     Будет создан целевой объект с именем HelloWorld. Обратите внимание, что во время редактирования файла проекта доступна поддержка Intellisense.  
  
2.  Добавьте строки в целевой объект HelloWorld, чтобы в результате раздел выглядел следующим образом:  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Hello"></Message>  <Message Text="World"></Message>  
    </Target>  
    ```  
  
3.  Сохраните файл проекта.  
  
 Задача Message является одной из многих, входящих в комплект поставки MSBuild. Полный список доступных задач и сведения об их использовании см. в статье [Task Reference](../msbuild/msbuild-task-reference.md) (Справочные сведения о задачах).  
  
 Задача Message принимает строковое значение атрибута Text в качестве входных данных и отображает его в устройстве вывода. Целевой объект HelloWorld выполняет задачу Message дважды: сначала для отображения Hello, а затем для отображения World.  
  
## <a name="building-the-target"></a>Создание целевого объекта  
 Запустите MSBuild из **командной строки Visual Studio**, чтобы создать целевой объект HelloWorld, определенный выше. Используйте параметр /target или /t для выбора целевого объекта.  
  
> [!NOTE]
>  В следующих разделах мы будем называть **командную строку Visual Studio** **командным окном**.  
  
#### <a name="to-build-the-target"></a>Создание целевого объекта  
  
1.  Нажмите кнопку **Пуск**, а затем выберите компонент **Все программы**. Найдите и щелкните **командную строку Visual Studio** в папке **Инструменты Visual Studio**.  
  
2.  В командном окне перейдите в папку, содержащую файл проекта. В данном случае это D:\BuildApp\BuildApp.  
  
3.  Выполните команду msbuild с параметром /t:HelloWorld. Будет выбран и создан целевой объект HelloWorld:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Изучите выходные данные в **окне командной строки**. Вы должны увидеть две строки — Hello и World:  
  
    ```  
    Hello  
    World  
    ```  
  
> [!NOTE]
>  Если вместо них вы видите `The target "HelloWorld" does not exist in the project`, возможно, вы забыли сохранить файл проекта в редакторе кода. Сохраните файл и повторите попытку.  
  
 Переключаясь между редактором кода и командной строкой, можно изменять файл проекта и сразу же видеть результаты.  
  
> [!NOTE]
>  Если команда msbuild выполняется без параметра /t, создается целевой объект, заданный атрибутом DefaultTarget элемента Project, в данном случае — Build. Будет собрано приложение Windows Forms BuildApp.exe.  
  
## <a name="build-properties"></a>Свойства сборки  
 Свойства сборки являются парами "имя — значение", управляющими сборкой. В верхней части файла проекта уже определено несколько свойств сборки:  
  
```xml  
<PropertyGroup>  
...  
  <ProductVersion>10.0.11107</ProductVersion>  
  <SchemaVersion>2.0</SchemaVersion>  
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>  
  <OutputType>WinExe</OutputType>  
...  
</PropertyGroup>  
```  
  
 Все свойства являются дочерними элементами по отношению к элементам PropertyGroup. Имя свойства — это имя дочернего элемента, а значение свойства — это текстовый элемент дочернего элемента. Например:  
  
```xml  
<TargetFrameworkVersion>v12.0</TargetFrameworkVersion>  
```  
  
 определяет свойство с именем TargetFrameworkVersion, задавая ему строковое значение v12.0.  
  
 Свойства сборки можно переопределить в любое время. If  
  
```xml  
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
```  
  
 появляется далее в файле проекта или в файле, позже импортированном в файл проекта, свойство TargetFrameworkVersion принимает новое значение v3.5.  
  
## <a name="examining-a-property-value"></a>Анализ значения свойства  
 Чтобы получить значение свойства, используйте следующий синтаксис, где PropertyName — имя свойства:  
  
```  
$(PropertyName)  
```  
  
 С помощью этого синтаксиса проанализируйте некоторые свойства в файле проекта.  
  
#### <a name="to-examine-a-property-value"></a>Анализ значения свойства  
  
1.  В редакторе кода замените целевой объект HelloWorld следующим кодом:  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Configuration is $(Configuration)" />  
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />  
    </Target>  
    ```  
  
2.  Сохраните файл проекта.  
  
3.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Проанализируйте результат. Вы должны увидеть следующие две строки (ваша версия .NET Framework может быть другой):  
  
    ```  
    Configuration is Debug  
    MSBuildToolsPath is C:\Program Files\MSBuild\12.0\bin  
    ```  
  
> [!NOTE]
>  Если вы не видите эти строки, возможно, вы забыли сохранить файл проекта в редакторе кода. Сохраните файл и повторите попытку.  
  
### <a name="conditional-properties"></a>Условные свойства  
 Многие свойства, например Configuration, определяются условно, то есть в элементе свойства отображается атрибут Condition. Условные свойства определяются или переопределяются только в том случае, если условие принимает значение true. Обратите внимание, что неопределенные свойства получают значение по умолчанию — пустую строку. Например:  
  
```xml  
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 означает: "Если свойство Configuration еще не определено, определите его и присвойте ему значение Debug".  
  
 Атрибут Condition может быть почти у всех элементов MSBuild. Дополнительные сведения об использовании атрибута Condition см. в статье об [условиях](../msbuild/msbuild-conditions.md).  
  
### <a name="reserved-properties"></a>Зарезервированные свойства  
 MSBuild резервирует некоторые имена свойств для хранения сведений о файле проекта и двоичных файлах MSBuild. Примером зарезервированного свойства является MSBuildToolsPath. Зарезервированные свойства указываются с символом $, как и любое другое свойство. Дополнительные сведения см. в статьях [How to: Reference the Name or Location of the Project File](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) (Практическое руководство. Использование ссылки на имя или расположение файла проекта) и [MSBuild Reserved and Well-Known Properties](../msbuild/msbuild-reserved-and-well-known-properties.md) (Зарезервированные и стандартные свойства MSBuild).  
  
### <a name="environment-variables"></a>Переменные среды  
 Ссылаться на переменные среды в файлах проектов можно так же, как на свойства сборки. Например, чтобы использовать переменную среды PATH в файле проекта, примените $(Path). Если проект содержит определение свойства с тем же именем, что и у переменной среды, свойство в проекте переопределит значение переменной среды. Дополнительные сведения см. в статье [How to: Use Environment Variables in a Build](../msbuild/how-to-use-environment-variables-in-a-build.md) (Практическое руководство. Использование переменных среды в сборке).  
  
## <a name="setting-properties-from-the-command-line"></a>Задание свойств из командной строки  
 Свойства можно определить в командной строке с помощью параметра /property или /p. Значения свойств, полученные из командной строки, переопределяют значения свойств, заданные в файле проекта и переменных среды.  
  
#### <a name="to-set-a-property-value-from-the-command-line"></a>Задание значения свойства из командной строки  
  
1.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release  
    ```  
  
2.  Проанализируйте результат. Вы должны увидеть следующую строку:  
  
    ```  
    Configuration is Release.  
    ```  
  
 MSBuild создает свойство Configuration и присваивает ему значение Release.  
  
## <a name="special-characters"></a>Специальные символы  
 Некоторые символы имеют особое значение в файлах проекта MSBuild. К ним относятся точка с запятой (;) и звездочка (*). Чтобы использовать эти специальные символы в качестве литералов в файле проекта, их необходимо задать с помощью синтаксиса % xx, где xx представляет шестнадцатеричное значение ASCII символа.  
  
 Измените задачу Message, чтобы отображать значение свойства Configuration со специальными символами для удобства чтения.  
  
#### <a name="to-use-special-characters-in-the-message-task"></a>Использование специальных символов в задаче Message  
  
1.  В редакторе кода замените обе задачи Message следующей строкой:  
  
    ```xml  
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />  
    ```  
  
2.  Сохраните файл проекта.  
  
3.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Проанализируйте результат. Вы должны увидеть следующую строку:  
  
    ```  
    $(Configuration) is "Debug"  
    ```  
  
 Дополнительные сведения см. в статье [MSBuild Special Characters](../msbuild/msbuild-special-characters.md) (Специальные символы MSBuild).  
  
## <a name="build-items"></a>Элементы сборки  
 Элемент — это часть данных, обычно имя файла, которая используется в качестве входных данных для системы сборки. Например, коллекцию элементов, представляющую исходные файлы, можно передать в задачу Compile, чтобы скомпилировать их в сборку.  
  
 Все элементы являются дочерними элементами по отношению к элементам ItemGroup. Именем элемента является имя дочернего элемента, а значением — значение атрибута Include дочернего элемента. Значения элементов с одинаковым именем собираются в типы элементов с таким именем.  Например:  
  
```xml  
<ItemGroup>  
    <Compile Include="Program.cs" />  
    <Compile Include="Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 определяет группу элементов, содержащую два элемента. Тип элемента Compile имеет два значения: Program.cs и Properties\AssemblyInfo.cs.  
  
 Следующий код создает тот же тип элементов посредством объявления обоих файлов в одном атрибуте Include, разделенных точкой с запятой.  
  
```xml  
<ItemGroup>  
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 Дополнительные сведения см. в статье [Элементы](../msbuild/msbuild-items.md).  
  
> [!NOTE]
>  Пути к файлам указаны относительно папки, содержащей файл проекта MSBuild.  
  
## <a name="examining-item-type-values"></a>Анализ значений типа элемента  
 Чтобы получить значения типа элемента, используйте следующий синтаксис, где ItemType — это имя типа элемента:  
  
```  
@(ItemType)  
```  
  
 С помощью этого синтаксиса проанализируйте тип элемента Compile в файле проекта.  
  
#### <a name="to-examine-item-type-values"></a>Анализ значений типа элемента  
  
1.  В редакторе кода замените целевую задачу HelloWorld следующим кодом:  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Compile item type contains @(Compile)" />  
    </Target>  
    ```  
  
2.  Сохраните файл проекта.  
  
3.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Проанализируйте результат. Вы должны увидеть следующую строку:  
  
    ```  
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs  
    ```  
  
 По умолчанию значения типа элемента разделены точкой с запятой.  
  
 Чтобы изменить разделитель типа элемента, используйте следующий синтаксис, где ItemType — это тип элемента, а Separator — это строка из одного или нескольких разделительных символов:  
  
```  
@(ItemType, Separator)  
```  
  
 Измените задачу Message для использования символов возврата каретки и перевода строки (%0A%0D) для отображения элементов Compile по одному в строке.  
  
#### <a name="to-display-item-type-values-one-per-line"></a>Отображение значений типов элементов по одному в строке  
  
1.  В редакторе кода замените задачу Message следующей строкой:  
  
    ```xml  
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />  
    ```  
  
2.  Сохраните файл проекта.  
  
3.  В **командном окне** введите и выполните следующую строку:  
  
     `msbuild buildapp.csproj /t:HelloWorld`  
  
4.  Проанализируйте результат. Должны отобразиться следующие строки:  
  
    ```  
    Compile item type contains Form1.cs  
    Form1.Designer.cs  
    Program.cs  
    Properties\AssemblyInfo.cs  
    Properties\Resources.Designer.cs  
    Properties\Settings.Designer.cs  
    ```  
  
### <a name="include-exclude-and-wildcards"></a>Атрибуты Include, Exclude и подстановочные знаки  
 Можно использовать подстановочные знаки "*", "\*\*" и "?" с атрибутом Include, чтобы добавить элементы к типу элемента. Например:  
  
```xml  
<Photos Include="images\*.jpeg" />  
```  
  
 добавляет все файлы с расширением файла .jpeg в папке изображений к типу элемента Photos, тогда как  
  
```xml  
<Photos Include="images\**.jpeg" />  
```  
  
 добавляет все файлы с расширением файла .jpeg в папке изображений и всех ее вложенных папках к типу элемента Photos. Дополнительные примеры см. в статье [How to: Select the Files to Build](../msbuild/how-to-select-the-files-to-build.md) (Практическое руководство. Выбор файлов для сборки).  
  
 Обратите внимание, что, так как элементы объявлены, они добавляются к типу элемента. Например:  
  
```xml  
<Photos Include="images\*.jpeg" />  
<Photos Include="images\*.gif" />  
```  
  
 создает тип элемента Photo, содержащий все файлы в папке изображений с расширением .jpeg или .gif. Это эквивалентно следующей строке:  
  
```xml  
<Photos Include="images\*.jpeg;images\*.gif" />  
```  
  
 С помощью атрибута Exclude можно исключить элемент из типа элемента. Например:  
  
```xml  
<Compile Include="*.cs" Exclude="*Designer*">  
```  
  
 добавляет все файлы с расширением .cs в тип элемента Compile типа, за исключением файлов, имена которых содержат строку Designer. Дополнительные сведения см. в статье [How to: Exclude Files from the Build](../msbuild/how-to-exclude-files-from-the-build.md) (Практическое руководство. Исключение файлов из сборки).  
  
 Атрибут Exclude применяется только к элементам, добавленным с помощью атрибута Include в элемент, содержащий их оба. Например:  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 не исключит файл Form1.cs, добавленный в предыдущий элемент.  
  
##### <a name="to-include-and-exclude-items"></a>Включение и исключение элементов  
  
1.  В редакторе кода замените задачу Message следующей строкой:  
  
    ```xml  
    <Message Text="Compile item type contains @(XFiles)" />  
    ```  
  
2.  Добавьте эту группу элементов сразу после элемента Import:  
  
    ```xml  
    <ItemGroup>  
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />  
    </ItemGroup>  
    ```  
  
3.  Сохраните файл проекта.  
  
4.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
5.  Проанализируйте результат. Вы должны увидеть следующую строку:  
  
    ```  
    Compile item type contains Form1.cs;Program.cs;Properties/Resources.resx  
    ```  
  
## <a name="item-metadata"></a>Метаданные элементов  
 Помимо сведений, собранных из атрибутов Include и Exclude, элементы могут содержать метаданные. Эти метаданные могут использоваться задачами, требующими дополнительных сведений об элементах, а не просто их значений.  
  
 Для объявления элементов в файле проекта создается элемент с именем метаданных, являющийся дочерним по отношению к элементу. Элемент может содержать нуль или более значений метаданных. Например, следующий элемент CSFile содержит метаданные Culture со значением Fr:  
  
```xml  
<ItemGroup>  
    <CSFile Include="main.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Чтобы получить значение метаданных типа элемента, используйте следующий синтаксис, где ItemType — это имя типа элементов, а MetaDataName — имя метаданных:  
  
```  
%(ItemType.MetaDataName)  
```  
  
#### <a name="to-examine-item-metadata"></a>Анализ метаданных элементов  
  
1.  В редакторе кода замените задачу Message следующей строкой:  
  
    ```xml  
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />  
    ```  
  
2.  Сохраните файл проекта.  
  
3.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Проанализируйте результат. Должны отобразиться следующие строки:  
  
    ```  
    Compile.DependentUpon:  
    Compile.DependentUpon: Form1.cs  
    Compile.DependentUpon: Resources.resx  
    Compile.DependentUpon: Settings.settings  
    ```  
  
 Обратите внимание, что фраза Compile.DependentUpon появляется несколько раз. Использование метаданных с таким синтаксисом в целевом объекте приводит к пакетной обработке. Пакетная обработка означает, что задачи в целевом объекте выполняются один раз для каждого уникального значения метаданных. Это является эквивалентом скрипта MSBuild общей конструкции программирования for loop. Дополнительные сведения см. в статье [Пакетная обработка](../msbuild/msbuild-batching.md).  
  
### <a name="well-known-metadata"></a>Стандартные метаданные  
 Всякий раз, когда элемент добавляется в список элементов, ему назначаются некоторые стандартные метаданные. Например %(Filename) возвращает имя файла любого элемента. Полный список стандартных метаданных см. в статье [Well-known Item Metadata](../msbuild/msbuild-well-known-item-metadata.md) (Стандартные метаданные элементов).  
  
##### <a name="to-examine-well-known-metadata"></a>Анализ стандартных метаданных  
  
1.  В редакторе кода замените задачу Message следующей строкой:  
  
    ```xml  
    <Message Text="Compile Filename: %(Compile.Filename)" />  
    ```  
  
2.  Сохраните файл проекта.  
  
3.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Проанализируйте результат. Должны отобразиться следующие строки:  
  
    ```  
    Compile Filename: Form1  
    Compile Filename: Form1.Designer  
    Compile Filename: Program  
    Compile Filename: AssemblyInfo  
    Compile Filename: Resources.Designer  
    Compile Filename: Settings.Designer  
    ```  
  
 Сравнивая два приведенных выше примера, можно увидеть, что, хотя не у каждого элемента в типе элемента Compile имеются метаданные DependentUpon, у всех элементов есть стандартные метаданные Filename.  
  
### <a name="metadata-transformations"></a>Преобразования метаданных  
 Списки элементов могут быть преобразованы в новые списки элементов. Чтобы преобразовать список элементов, используйте следующий синтаксис, где ItemType — это имя типа элементов, а MetadataName — имя метаданных:  
  
```  
@(ItemType -> '%(MetadataName)')  
```  
  
 Например, список элементов исходных файлов можно преобразовать в коллекцию объектных файлов с помощью выражения `@(SourceFiles -> '%(Filename).obj')`. Дополнительные сведения см. в статье [Преобразования](../msbuild/msbuild-transforms.md).  
  
##### <a name="to-transform-items-using-metadata"></a>Преобразование элементов с помощью метаданных  
  
1.  В редакторе кода замените задачу Message следующей строкой:  
  
    ```xml  
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />  
    ```  
  
2.  Сохраните файл проекта.  
  
3.  В **командном окне** введите и выполните следующую строку:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Проанализируйте результат. Вы должны увидеть следующую строку:  
  
    ```  
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak  
    ```  
  
 Обратите внимание, что выраженные в этом синтаксисе метаданные не приводят к пакетной обработке.  
  
## <a name="whats-next"></a>Что дальше?  
 Сведения о пошаговом создании файла простого проекта см. в статье [Walkthrough: Creating an MSBuild Project File from Scratch](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) (Пошаговое руководство. Создание файла проекта MSBuild с нуля).  
  
## <a name="see-also"></a>См. также
[MSBuild Overview](../msbuild/msbuild.md) (Общие сведения о MSBuild)  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
