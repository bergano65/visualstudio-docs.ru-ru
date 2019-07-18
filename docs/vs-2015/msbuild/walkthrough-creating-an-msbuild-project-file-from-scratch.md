---
title: Пошаговое руководство. Создание файла проекта MSBuild с нуля | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb49e6c51c1e51d002683099797d940cb2d24556
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682362"
---
# <a name="walkthrough-creating-an-msbuild-project-file-from-scratch"></a>Пошаговое руководство. Создание файла проекта MSBuild с нуля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Языки программирования, предназначенные для платформы .NET Framework, используют файлы проекта MSBuild для описания и контроля процесса построения приложения. Если для создания файла проекта MSBuild используется Visual Studio, соответствующий XML добавляется в файл автоматически. Тем не менее, понимание принципов организации XML и способов его изменения, позволяющих контролировать построение, может вам пригодиться.  
  
 Сведения о создании файла проекта для проекта C++ см. в разделе [MSBuild (Visual C++)](https://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Это пошаговое руководство содержит описание способов создания основного файла с использованием только текстового редактора. Руководство включает следующие шаги.  
  
- Создание минимального исходного файла приложения.  
  
- Создание минимального файла проекта MSBuild.  
  
- Расширение переменной среды PATH для включения MSBuild.  
  
- Построение приложения с помощью файла проекта.  
  
- Добавление свойств для управления построением.  
  
- Управление построением с помощью изменений значений свойства.  
  
- Добавление целей к построению.  
  
- Управление построением путем указания целей.  
  
- Последовательное построение.  
  
  В этом пошаговом руководстве показан способ построения проекта в командной строке и проверка результатов. Дополнительные сведения о платформе MSBuild и ее запуске из командной строки см. в статье [Пошаговое руководство. Использование MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
  Для выполнения пошагового руководства необходимо установить платформу .NET Framework версии 2.0, 3.5, 4.0 или 4.5 — она включает MSBuild и компилятор Visual C#.  
  
## <a name="creating-a-minimal-application"></a>Создание минимального приложения  
 Этот раздел описывает процедуру создания исходного файла минимального приложения Visual C# с помощью текстового редактора.  
  
#### <a name="to-create-the-minimal-application"></a>Создание минимального приложения  
  
1. В командной строке перейдите к папке, в которой необходимо создать приложение, например \Мои документы\ или \Рабочий стол\\.  
  
2. Введите **md HelloWorld**, чтобы создать подпапку \Helloworld\\.  
  
3. Введите **cd HelloWorld**, чтобы изменить новую папку.  
  
4. Запустите "Блокнот" или другой текстовый редактор и введите следующий код.  
  
    ```  
    using System;  
  
    class HelloWorld  
    {  
        static void Main()  
        {  
    #if DebugConfig  
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");  
    #endif  
  
            Console.WriteLine("Hello, world!");  
        }  
    }  
    ```  
  
5. Сохраните файл исходного кода и назовите его Helloworld.cs.  
  
6. Создайте приложение, указав в командной строке **csc helloworld.cs**.  
  
7. Проверьте приложение, указав в командной строке **helloworld**.  
  
     Должно появиться сообщение **Hello, world!** .  
  
8. Удалите приложение, указав в командной строке **del helloworld.exe**.  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>Создание минимального файла проекта MSBuild  
 Теперь, когда у вас есть минимальный исходный файл приложения, вы можете создать минимальный файл проекта для построения приложения. Такой файл проекта содержит следующие элементы.  
  
- Необходимый корневой узел `Project`.  
  
- Узел `ItemGroup` для хранения элементов.  
  
- Элемент, который ссылается на исходный файл приложения.  
  
- Узел `Target` для хранения задач, которые требуются для построения приложения.  
  
- Элемент `Task` для запуска компилятора Visual C# для построения приложения.  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>Создание файла минимального проекта MSBuild  
  
1. В текстовом редакторе замените существующий текст с помощью следующих двух строк:  
  
   ```  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   </Project>  
   ```  
  
2. Вставьте следующий узел `ItemGroup` в качестве дочернего элемента узла `Project`:  
  
   ```  
   <ItemGroup>  
     <Compile Include="helloworld.cs" />  
   </ItemGroup>  
   ```  
  
    Обратите внимание, что узел `ItemGroup` уже содержит элемент.  
  
3. Добавьте узел `Target` в качестве дочернего элемента узла `Project`. Назовите узел `Build`.  
  
   ```  
   <Target Name="Build">  
   </Target>  
   ```  
  
4. Вставьте следующий элемент задачи в качестве дочернего элемента узла `Target`.  
  
   ```  
   <Csc Sources="@(Compile)"/>  
   ```  
  
5. Сохраните этот файл проекта и назовите его Helloworld.csproj.  
  
   Минимальный файл проекта должен выглядеть следующим образом:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  
  
 Задачи в целевом объекте сборки выполняются последовательно. В этом случае задача `Csc` компилятора Visual C# является единственной. Она ожидает список исходных файлов для компилирования, который задается значением элемента `Compile`. Элемент `Compile` ссылается на единственный исходный файл Helloworld.cs.  
  
> [!NOTE]
> В элементе можно использовать подстановочный знак (*) для ссылки на все файлы, которые имеют расширение имени файла .CS:  
>   
> `<Compile Include="*.cs" />`  
>   
> Тем не менее мы не рекомендуем использовать подстановочные знаки, так как это создает сложности при отладке и постановке выборочных задач в случае добавления или удаления исходных файлов.  
  
## <a name="extending-the-path-to-include-msbuild"></a>Расширение пути для включения MSBuild  
 Прежде чем получить доступ к MSBuild, необходимо расширить переменную среду PATH для включения папки .NET Framework.  
  
#### <a name="to-add-msbuild-to-your-path"></a>Добавление MSBuild к пути  
  
- Начиная с Visual Studio 2013, файл MSBuild.exe находится в папке MSBuild (`%ProgramFiles%\MSBuild` 32-разрядной операционной системы или `%ProgramFiles(x86)%\MSBuild` 64-разрядной операционной системы).  
  
     В командной строке введите **set PATH= %PATH %; %ProgramFiles %\MSBuild** или **set PATH= %PATH %; %ProgramFiles(x86) %\MSBuild**.  
  
     Если на вашем компьютере установлено ПО Visual Studio, воспользуйтесь **командной строкой Visual Studio**, где имеется путь с указанием папки MSBuild.  
  
## <a name="using-the-project-file-to-build-the-application"></a>Использование файла проекта для построения приложения  
 Теперь используйте только что созданный файл проекта для построения приложения.  
  
#### <a name="to-build-the-application"></a>Построение приложения  
  
1. В командной строке введите **msbuild helloworld.csproj /t:Build**.  
  
     После этого для создания приложения "Helloworld" будет вызван компилятор Visual C# и построен целевой объект построения файла проекта Helloworld.  
  
2. Протестируйте приложение, указав в командной строке **helloworld**.  
  
     Должно появиться сообщение **Hello, world!** .  
  
> [!NOTE]
> Чтобы получить более подробную информацию о построении, увеличьте уровень детализации. Чтобы изменить уровень детализации на "подробный", введите в командную строку одну из следующих команд:  
>   
> **msbuild helloworld.csproj /t:Build /verbosity:detailed**  
  
## <a name="adding-build-properties"></a>Добавление свойств сборки  
 Для дальнейшего управления построением можно добавлять свойства построения к файлу проекта. Добавьте следующие свойства.  
  
- Свойство `AssemblyName`, чтобы указать имя приложения.  
  
- Свойство `OutputPath`, чтобы указать папку для хранения приложения.  
  
#### <a name="to-add-build-properties"></a>Добавление свойств построения  
  
1. Удалите существующее приложение, указав в командной строке **del helloworld.exe**.  
  
2. В файле проекта вставьте этот элемент `PropertyGroup` сразу после начала элемента `Project`:  
  
   ```  
   <PropertyGroup>  
     <AssemblyName>MSBuildSample</AssemblyName>  
     <OutputPath>Bin\</OutputPath>  
   </PropertyGroup>  
   ```  
  
3. Добавьте задачу в целевой объект построения непосредственно перед задачей `Csc`:  
  
   ```  
   <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
   ```  
  
    Задача `MakeDir` создает папку, которой присваивается имя свойства `OutputPath`, при условии, что папка с таким именем не существует.  
  
4. Добавьте следующий атрибут `OutputAssembly` к задаче `Csc`:  
  
   ```  
   <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
   ```  
  
    Он поручает компилятору Visual C# создать сборку, присвоить ей имя свойства `AssemblyName` и вставить в папку, которой присвоено имя свойства `OutputPath`.  
  
5. Сохраните изменения.  
  
   Файл проекта должен выглядеть следующим образом:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
</Project>  
```  
  
> [!NOTE]
> Мы рекомендуем добавить разделитель пути в виде обратной косой черты (\\) в конце имени папки при его указании в элементе `OutputPath`, вместо добавления его в атрибут `OutputAssembly` задачи `Csc`. Поэтому  
>   
> `<OutputPath>Bin\</OutputPath>`  
>   
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
> лучше, чем  
>   
> `<OutputPath>Bin</OutputPath>`  
>   
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="testing-the-build-properties"></a>Тестирование свойств построения  
 Теперь вы можете построить приложение с использованием файла проекта, в котором использовались свойства построения, и указать папку вывода и имя приложения.  
  
#### <a name="to-test-the-build-properties"></a>Тестирование свойств построения  
  
1. В командной строке введите **msbuild helloworld.csproj /t:Build**.  
  
     После этого программа создаст папку \Bin\, вызовет компилятор Visual C# для создания приложения MSBuildSample и разместит его в папку \Bin\.  
  
2. Чтобы убедиться, что папка \Bin\ создана и содержит приложение MSBuildSample, введите **dir Bin**.  
  
3. Протестируйте приложение, указав в командной строке **Bin\MSBuildSample**.  
  
     Должно появиться сообщение **Hello, world!** .  
  
## <a name="adding-build-targets"></a>Добавление целей сборки  
 Теперь добавьте к файлу проекта еще две цели.  
  
- Цель "Очистить", которая удаляет старые файлы.  
  
- Цель "Перестроить", которая использует атрибут `DependsOnTargets` для принудительного запуска задачи "Очистить" перед выполнением задачи "Построение".  
  
  Теперь, когда целей несколько, можно задать в качестве цели по умолчанию цель "Построение".  
  
#### <a name="to-add-build-targets"></a>Добавление целей построения  
  
1. В файле проекта добавьте эти две цели сразу после цели "Построение":  
  
   ```  
   <Target Name="Clean" >  
     <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
   </Target>  
   <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
   ```  
  
    Цель "Очистить" вызывает задачу "Удалить", чтобы удалить приложение. Цель "Перестроить" не запускается, пока не будут выполнены цели "Очистить" и "Построение". Несмотря на то, что цель "Перестроить" не имеет задач, она вызывает выполнение цели "Очистить" до выполнения цели "Построение".  
  
2. Добавьте следующий атрибут `DefaultTargets` в начало элемента `Project`:  
  
   ```  
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   ```  
  
    Это сделает цель "Построение" целью по умолчанию.  
  
   Файл проекта должен выглядеть следующим образом:  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Clean" >  
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
</Project>  
```  
  
## <a name="testing-the-build-targets"></a>Тестирование целей построения  
 Для тестирования этих функций файла проекта можно запустить новые цели построения.  
  
- Построение по умолчанию.  
  
- Задание имени приложения в командной строке.  
  
- Удаление приложения перед построением другого приложения.  
  
- Удаление приложения без построения другого приложения.  
  
#### <a name="to-test-the-build-targets"></a>Тестирование целей построения  
  
1. В командной строке введите **msbuild helloworld.csproj /p:AssemblyName=Greetings**.  
  
     Так как параметр **/t** для задания цели напрямую не использовался, MSBuild запускает цель "Сборка" по умолчанию. Параметр **/p** переопределяет свойство `AssemblyName` и присваивает ему новое значение `Greetings`. В результате в папке \Bin\ создается новое приложение Greetings.exe.  
  
2. Чтобы убедиться, что в папке \Bin\ находится приложение MSBuildSample и новое приложение Greetings, введите **dir Bin**.  
  
3. Протестируйте приложение Greetings, указав в командной строке **Bin\Greetings**.  
  
     Должно появиться сообщение **Hello, world!** .  
  
4. Удалите приложение MSBuildSample, указав **msbuild helloworld.csproj /t:clean**.  
  
     Это запустит задачу "Очистить" и позволит удалить приложение со значением свойства `AssemblyName` по умолчанию — `MSBuildSample`.  
  
5. Удалите приложение Greetings, указав **msbuild helloworld.csproj /t:clean /p:AssemblyName=Greetings**.  
  
     Это запустит задачу "Очистить" и позволит удалить приложение с заданным значением свойства **AssemblyName** по умолчанию — `Greetings`.  
  
6. Чтобы убедиться, что папка \Bin\ пуста, введите **dir Bin**.  
  
7. Введите команду **msbuild**.  
  
     Несмотря на то что файл проекта не указан, MSBuild строит файл helloworld.csproj, поскольку в текущей папке присутствует только один файл проекта. В результате в папке \Bin\ создается новое приложение MSBuildSample.  
  
     Чтобы убедиться, что в папке \Bin\ появилось приложение MSBuildSample, введите **dir Bin**.  
  
## <a name="building-incrementally"></a>Последовательное построение  
 MSBuild можно настроить таким образом, чтобы цель строилась только в случае изменения исходного файла или целевых файлов, от которых зависит цель. MSBuild определяет факт изменения файла по отметке времени.  
  
#### <a name="to-build-incrementally"></a>Последовательное построение  
  
1. В файле проекта добавьте к открытой цели "Построение" следующие два атрибута:  
  
    ```  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     Они показывают, что цель "Построение" зависит от входных файлов, указанных в группе элементов `Compile`, и что цель вывода является файлом приложения.  
  
     Полученная цель "Построение" должна выглядеть следующим образом:  
  
    ```  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2. Протестируйте цель "Сборка", указав в командной строке **msbuild /v:d**.  
  
     Помните, что helloworld.csproj является файлом проекта по умолчанию, а построение — целью по умолчанию.  
  
     Параметр **/v:d** указывает подробное описание для процесса сборки.  
  
     На экране должны появиться следующие строки:  
  
     **Целевой объект "Сборка" пропускается, так как все выходные файлы актуальны по отношению к входным.**  
  
     **Входные файлы: HelloWorld.cs**  
  
     **Выходные файлы: BinMSBuildSample.exe**  
  
     MSBuild пропускает цель "Построение", так как с последнего построения приложения ни один из исходных файлов не изменился.  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показан файл проекта, который компилирует приложение [!INCLUDE[csprcs](../includes/csprcs-md.md)] и записывает сообщение, содержащее имя файла вывода.  
  
### <a name="code"></a>Код  
  
```csharp  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files of type CSFile -->  
        <CSC  
            Sources = "@(CSFile)"  
            OutputAssembly = "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Комментарии  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показан файл проекта, который компилирует приложение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] и записывает сообщение, содержащее имя файла вывода.  
  
### <a name="code"></a>Код  
  
```vb  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldVB</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <VBFile Include = "consolehwvb1.vb"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">      
        <!-- Run the Visual Basic compilation using input files of type VBFile -->  
        <VBC  
            Sources = "@(VBFile)"  
            OutputAssembly= "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the VBC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </VBC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="whats-next"></a>Что дальше?  
 Visual Studio может выполнять большую часть работы, описанной в этом пошаговом руководстве, автоматически. Сведения об использовании Visual Studio для создания, изменения, сборки и тестирования файлов проекта MSBuild см. в разделе [Пошаговое руководство. Использование MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="see-also"></a>См. также раздел  
[MSBuild Overview](msbuild.md) (Общие сведения о MSBuild)  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
