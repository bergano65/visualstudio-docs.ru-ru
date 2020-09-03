---
title: Создание базовой системы проектов, часть 1 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20637fb47d85b7cb8341df22d056ffe44534835f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295483"
---
# <a name="creating-a-basic-project-system-part-1"></a>Создание системы базового проекта. Часть 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio проекты — это контейнеры, используемые разработчиками для организации файлов исходного кода и других ресурсов. Проекты отображаются как дочерние элементы решений в **Обозреватель решений**. Проекты позволяют упорядочивать, собирать, отлаживать и развертывать исходный код и создавать ссылки на веб-службы, базы данных и другие ресурсы.  
  
 Проекты определяются в файлах проекта, например CSPROJ-файл для проекта Visual C#. Можно создать собственный тип проекта с расширением имени файла проекта. Дополнительные сведения о типах проектов см. в разделе [типы проектов](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Если необходимо расширить Visual Studio с помощью пользовательского типа проекта, мы настоятельно рекомендуем использовать [систему проектов Visual Studio](https://github.com/Microsoft/VSProjectSystem) , имеющую ряд преимуществ по сравнению с созданием системы проектов с нуля.  
> 
> - Упрощение адаптации.  Даже для базовой системы проектов требуется десятка тысяч строк кода.  Благодаря использованию CPS стоимость адаптации уменьшается до нескольких щелчков, прежде чем вы сможете настроить ее в своих нуждах.  
>   - Более простое обслуживание.  Используя CPS, необходимо поддерживать только собственные сценарии.  Мы работаем над отработкой всей инфраструктуры системы проектов.  
> 
>   Если вам нужно использовать версии Visual Studio более ранние, чем Visual Studio 2013, вы не сможете воспользоваться сервером публикаций Contribute в расширении Visual Studio.  Если это так, это пошаговое руководство является хорошим местом для начала работы.  
  
 В этом пошаговом руководстве показано, как создать тип проекта с расширением имени файла проекта. мипрож. Это пошаговое руководство позаимствовано на основе существующей системы проектов Visual C#.  
  
> [!NOTE]
> Полный пример полной системы проекта языка см. в разделе примеры для IronPython, посвященные примерам [VSSDK](../misc/vssdk-samples.md).  
  
 В этом пошаговом руководстве объясняется, как выполнить эти задачи:  
  
- Создайте базовый тип проекта.  
  
- Создайте базовый шаблон проекта.  
  
- Зарегистрируйте шаблон проекта в Visual Studio.  
  
- Создайте экземпляр проекта, открыв диалоговое окно **Создание проекта** , а затем используя шаблон.  
  
- Создание фабрики проектов для системы проектов.  
  
- Создайте узел проекта для системы проектов.  
  
- Добавление пользовательских значков для системы проектов.  
  
- Реализуйте базовую подстановку параметров шаблона.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Также необходимо загрузить исходный код для [платформы управляемого пакета для проектов](https://archive.codeplex.com/?p=mpfproj12). Извлеките файл в расположение, доступное для решения, которое вы собираетесь создать.  
  
## <a name="creating-a-basic-project-type"></a>Создание базового типа проекта  
 Создайте проект VSIX C# с именем **симплепрожект**. (**Файл, создать, проект** , а затем — **C#, расширяемость, пакет Visual Studio**). Добавьте шаблон элемента проекта пакета Visual Studio (на обозреватель решений щелкните правой кнопкой мыши узел проекта и выберите **Добавить/новый элемент**, а затем — **расширяемость/пакет Visual Studio**). Назовите файл **симплепрожектпаккаже**.  
  
## <a name="creating-a-basic-project-template"></a>Создание базового шаблона проекта  
 Теперь можно изменить этот базовый пакет VSPackage, чтобы реализовать новый тип проекта. мипрож. Чтобы создать проект, основанный на типе проекта. мипрож, Visual Studio необходимо выяснить, какие файлы, ресурсы и ссылки нужно добавить в новый проект. Чтобы предоставить эти сведения, помещайте файлы проекта в папку шаблона проекта. Когда пользователь использует проект мипрож для создания проекта, файлы копируются в новый проект.  
  
#### <a name="to-create-a-basic-project-template"></a>Создание базового шаблона проекта  
  
1. Добавьте в проект три папки — один из следующих: **темплатес\прожектс\симплепрожект**. (В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта **симплепрожект** , наведите указатель на пункт **добавить**и выберите пункт **создать папку**. Назовите папку `Templates`. В папке **Templates** добавьте папку с именем `Projects` . В папке **проекты** добавьте папку с именем `SimpleProject` .)  
  
2. В папке **прожектс\симплепрожект** добавьте файл значка с именем `SimpleProject.ico` . При нажатии кнопки **Добавить**открывается Редактор значков.  
  
3. Сделайте значок отличительным. Этот значок будет отображаться в диалоговом окне " **Новый проект** " Далее в этом пошаговом руководстве.  
  
    ![Значок: значок простого проекта](../extensibility/media/simpleprojicon.png "симплепрожикон")  
  
4. Сохраните значок и закройте редактор значков.  
  
5. В папке **прожектс\симплепрожект** добавьте элемент **класса** с именем `Program.cs` .  
  
6. Замените существующий код следующими строками.  
  
   ```csharp  
   using System;  
   using System.Collections.Generic;  
   using System.Text;  
  
   namespace $nameSpace$  
   {  
       public class $className$  
       {  
           static void Main(string[] args)  
           {  
               Console.WriteLine("Hello VSX!!!");  
               Console.ReadKey();  
           }  
       }  
   }  
   ```  
  
   > [!IMPORTANT]
   > Это не последняя форма кода Program.cs; параметры замены будут обрабатываться на более позднем этапе. Вы можете увидеть ошибки компиляции, но при условии, что содержимое **файла** является **содержимым**, вы сможете создать и запустить проект обычным образом.  
  
7. Сохраните файл.  
  
8. Скопируйте файл AssemblyInfo.cs из папки **Properties** в папку **прожектс\симплепрожект** .  
  
9. В папке **прожектс\симплепрожект** добавьте XML-файл с именем `SimpleProject.myproj` .  
  
   > [!NOTE]
   > Расширение имени файла для всех проектов этого типа —. мипрож. Если вы хотите изменить его, его необходимо изменить везде, где он упоминается в этом пошаговом руководстве.  
  
10. Замените имеющееся содержимое следующими строками.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
11. Сохраните файл.  
  
12. В окне **Свойства** задайте для **действия сборки** AssemblyInfo.cs, Program.cs, Симплепрожект. ICO и Симплепрожект. мипрож значение **Content**и задайте для свойств **включить в VSIX** **значение true**.  
  
    Этот шаблон проекта описывает базовый проект Visual C# с конфигурацией отладки и конфигурацией выпуска. Проект включает два исходных файла, AssemblyInfo.cs и Program.cs, и несколько ссылок на сборки. При создании проекта на основе шаблона значение Прожектгуид автоматически заменяется новым идентификатором GUID.  
  
    В **Обозреватель решений**Расширенная папка **Templates** должна выглядеть следующим образом:  
  
    Шаблоны  
  
    Проекты  
  
    симплепрожект  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    Симплепрожект. ico  
  
    Симплепрожект. мипрож  
  
## <a name="creating-a-basic-project-factory"></a>Создание базовой фабрики проектов  
 Необходимо сообщить Visual Studio о расположении папки шаблона проекта. Для этого добавьте атрибут в класс VSPackage, реализующий фабрику проектов, чтобы расположение шаблона записывалось в системный реестр при построении VSPackage. Начните с создания базовой фабрики проектов, определяемой идентификатором GUID фабрики проектов. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут для подключения фабрики проектов к классу симплепрожектпаккаже.  
  
#### <a name="to-create-a-basic-project-factory"></a>Создание базовой фабрики проектов  
  
1. Откройте SimpleProjectPackageGuids.cs в редакторе кода.  
  
2. Создайте идентификаторы GUID для фабрики проектов (в меню **Сервис** выберите пункт **Создать GUID**) или используйте его в следующем примере. Добавьте идентификаторы GUID в класс Симплепрожектпаккажегуидс. Идентификаторы GUID должны быть в форме идентификатора GUID и в форме строки. Результирующий код должен выглядеть следующим образом.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. Добавьте класс в верхнюю папку **симплепрожект** с именем `SimpleProjectFactory.cs` .  
  
4. Добавьте операторы using:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Добавьте атрибут GUID в класс Симплепрожектфактори. Значением атрибута является новый идентификатор GUID фабрики проекта.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Теперь можно зарегистрировать шаблон проекта.  
  
#### <a name="to-register-the-project-template"></a>Регистрация шаблона проекта  
  
1. В SimpleProjectPackage.cs добавьте атрибут в <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> класс симплепрожектпаккаже, как показано ниже.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
    Перестроение регистрирует шаблон проекта.  
  
   Параметры и устанавливаются `defaultProjectExtension` `possibleProjectExtensions` в расширение имени файла проекта (. мипрож). `projectTemplatesDirectory`Для параметра задается относительный путь к папке Templates. Во время сборки этот путь будет преобразован в полную сборку и добавлен в реестр для регистрации системы проектов.  
  
## <a name="testing-the-template-registration"></a>Тестирование регистрации шаблона  
 Регистрация шаблона сообщает Visual Studio о расположении папки шаблонов проектов, чтобы Visual Studio могла отображать имя и значок шаблона в диалоговом окне **Новый проект** .  
  
#### <a name="to-test-the-template-registration"></a>Проверка регистрации шаблона  
  
1. Нажмите клавишу F5, чтобы начать отладку экспериментального экземпляра Visual Studio.  
  
2. В экспериментальном экземпляре создайте новый проект созданного типа проекта. В диалоговом окне **Новый проект** в разделе **Установленные шаблоны**должно отобразиться **симплепрожект** .  
  
   Теперь у вас есть зарегистрированная фабрика проектов. Однако он еще не может создать проект. Пакет проекта и фабрика проектов работают вместе для создания и инициализации проекта.  
  
## <a name="add-the-managed-package-framework-code"></a>Добавление кода платформы управляемого пакета  
 Реализуйте соединение между пакетом проекта и фабрикой проекта.  
  
- Импортируйте файлы исходного кода для платформы управляемого пакета.  
  
    1. Выгрузите проект Симплепрожект (в **Обозреватель решений**выберите узел проекта и в контекстном меню выберите команду **Выгрузить проект**) и откройте файл проекта в редакторе XML.  
  
    2. Добавьте следующие блоки в файл проекта (непосредственно над \<Import> блоками). Задайте для Прожектбасепас расположение файла Прожектбасе. Files в загруженном коде платформы управляемого пакета. Может потребоваться добавить в путь обратную косую черту. В противном случае проект может не найти код платформы управляемого пакета.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        > Не забывайте обратную косую черту в конце пути.  
  
    3. Перезагрузите проект.  
  
    4. Добавьте ссылки на следующие сборки:  
  
        - Microsoft. VisualStudio. Designer. Interfaces (в \<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft. Build. Tasks. v 4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Инициализация фабрики проектов  
  
1. Добавьте в файл SimpleProjectPackage.cs следующую `using` инструкцию.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. Создайте класс, производный `SimpleProjectPackage` от `Microsoft.VisualStudio.Package.ProjectPackage` .  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Зарегистрируйте фабрику проекта. Добавьте следующую строку в `SimpleProjectPackage.Initialize` метод сразу после `base.Initialize` .  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. Реализуйте абстрактное свойство `ProductUserContext` :  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. В SimpleProjectFactory.cs добавьте следующий `using` оператор после существующих `using` инструкций.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. Создайте класс, производный `SimpleProjectFactory` от `ProjectFactory` .  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Добавьте в класс следующий фиктивный метод `SimpleProjectFactory` . Этот метод будет реализован в следующем разделе.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Добавьте в класс следующее поле и конструктор `SimpleProjectFactory` . Эта `SimpleProjectPackage` ссылка кэшируется в частном поле, чтобы его можно было использовать при настройке сайта поставщика услуг.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
## <a name="testing-the-project-factory-implementation"></a>Тестирование реализации фабрики проектов  
 Проверьте, вызывается ли конструктор для реализации фабрики проектов.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Тестирование реализации фабрики проектов  
  
1. В файле SimpleProjectFactory.cs установите точку останова в следующей строке `SimpleProjectFactory` конструктора.  
  
    ```  
    this.package = package;  
    ```  
  
2. Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр Visual Studio.  
  
3. В экспериментальном экземпляре начните создавать новый проект. В диалоговом окне **Новый проект** выберите тип проекта симплепрожект и нажмите кнопку **ОК**. Выполнение прекратится в точке останова.  
  
4. Очистите точку останова и отключите отладку. Так как мы еще не создали узел проекта, код создания проекта по-прежнему создает исключения.  
  
## <a name="extending-the-project-node-class"></a>Расширение класса узла проекта  
 Теперь можно реализовать `SimpleProjectNode` класс, производный от `ProjectNode` класса. `ProjectNode`Базовый класс обрабатывает следующие задачи создания проекта:  
  
- Копирует файл шаблона проекта Симплепрожект. мипрож в папку нового проекта. Копия переименовывается в соответствии с именем, введенным в диалоговом окне **Новый проект** . `ProjectGuid`Значение свойства заменяется новым идентификатором GUID.  
  
- Обходят элементы MSBuild файла шаблона проекта Симплепрожект. мипрож и ищет `Compile` элементы. Для каждого `Compile` целевого файла копирует файл в папку нового проекта.  
  
  Производный `SimpleProjectNode` класс обрабатывает следующие задачи:  
  
- Включает создание или выбор значков для узлов проектов и файлов в **Обозреватель решений** .  
  
- Включает возможность указания дополнительных подстановок параметров шаблона проекта.  
  
#### <a name="to-extend-the-project-node-class"></a>Расширение класса узла проекта  
  
1. 
  
2. Добавьте класс с именем `SimpleProjectNode.cs`.  
  
3. Замените существующий код следующим кодом:  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Project;  
  
   namespace SimpleProject  
   {  
       public class SimpleProjectNode : ProjectNode  
       {  
           private SimpleProjectPackage package;  
  
           public SimpleProjectNode(SimpleProjectPackage package)  
           {  
               this.package = package;  
           }  
           public override Guid ProjectGuid  
           {  
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
           }  
           public override string ProjectType  
           {  
               get { return "SimpleProjectType"; }  
           }  
  
           public override void AddFileFromTemplate(  
               string source, string target)  
           {  
               this.FileTemplateProcessor.UntokenFile(source, target);  
               this.FileTemplateProcessor.Reset();  
           }  
       }  
   }  
   ```  
  
   Эта `SimpleProjectNode` Реализация класса имеет следующие переопределенные методы:  
  
- `ProjectGuid`, возвращающий идентификатор GUID фабрики проекта.  
  
- `ProjectType`, возвращающее локализованное имя типа проекта.  
  
- `AddFileFromTemplate`, который копирует выбранные файлы из папки шаблонов в целевой проект. Этот метод далее реализован в следующем разделе.  
  
  `SimpleProjectNode`Конструктор, как и `SimpleProjectFactory` конструктор, кэширует `SimpleProjectPackage` ссылку в закрытом поле для последующего использования.  
  
  Чтобы подключить `SimpleProjectFactory` класс к `SimpleProjectNode` классу, необходимо создать новый экземпляр `SimpleProjectNode` в `SimpleProjectFactory.CreateProject` методе и кэшировать его в частном поле для последующего использования.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Подключение класса фабрики проектов и класса Node  
  
1. В файле SimpleProjectFactory.cs добавьте следующую `using` инструкцию:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. Замените `SimpleProjectFactory.CreateProject` метод, используя следующий код.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Перестройте решение и убедитесь, что сборка выполняется без ошибок.  
  
## <a name="testing-the-project-node-class"></a>Тестирование класса узла проекта  
 Проверьте фабрику проекта, чтобы определить, создает ли она иерархию проектов.  
  
#### <a name="to-test-the-project-node-class"></a>Тестирование класса узла проекта  
  
1. Нажмите клавишу F5, чтобы начать отладку. В экспериментальном экземпляре создайте новый Симплепрожект.  
  
2. Visual Studio следует вызывать фабрику проектов для создания проекта.  
  
3. Закройте экспериментальный экземпляр Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Добавление пользовательского значка узла проекта  
 Значок узла проекта в предыдущем разделе является значком по умолчанию. Его можно изменить на пользовательский значок.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Добавление пользовательского значка узла проекта  
  
1. В папке **Resources** добавьте файл точечного рисунка с именем SimpleProjectNode.bmp.  
  
2. В окнах **свойств** Сократите точечный рисунок до 16 пикселов. Сделайте свой точечный рисунок.  
  
    ![Команда простого проекта](../extensibility/media/simpleprojprojectcomm.png "симплепрожпрожекткомм")  
  
3. В окне **Свойства** измените **действие сборки** точечного рисунка на **внедренный ресурс**.  
  
4. В SimpleProjectNode.cs добавьте следующие `using` инструкции:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Добавьте в класс следующее статическое поле и конструктор `SimpleProjectNode` .  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Добавьте следующее свойство в начало `SimpleProjectNode` класса.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Замените конструктор экземпляра следующим кодом.  
  
   ```  
   public SimpleProjectNode(SimpleProjectPackage package)  
   {  
       this.package = package;  
  
       imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
       foreach (Image img in imageList.Images)  
       {  
           this.ImageHandler.AddImage(img);  
       }  
   }  
   ```  
  
   Во время статической конструкции `SimpleProjectNode` получает битовую карту узла проекта из ресурсов манифеста сборки и кэширует ее в частном поле для последующего использования. Обратите внимание на синтаксис <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> пути к изображению. Чтобы просмотреть имена ресурсов манифеста, внедренных в сборку, используйте <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> метод. При применении этого метода к `SimpleProject` сборке результаты должны выглядеть следующим образом:  
  
- Симплепрожект. Resources. Resources  
  
- VisualStudio. Project. Resources  
  
- Симплепрожект. VSPackage. Resources  
  
- Resources.imagelis.bmp  
  
- Microsoft. VisualStudio. Project. Донтшовагаиндиалог. Resources  
  
- Microsoft. VisualStudio. Project. Секуритиварнингдиалог. Resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  Во время создания экземпляра `ProjectNode` базовый класс загружает Resources.imagelis.bmp, в которых часто используются 16 x 16 точечных рисунков из Resources\imagelis.bmp. Этот список растровых изображений доступен в `SimpleProjectNode` виде ImageHandler. ImageList. `SimpleProjectNode` Добавляет в список битовую карту узла проекта. Смещение растрового изображения узла проекта в списке изображений кэшируется для последующего использования в качестве значения общего `ImageIndex` Свойства. Visual Studio использует это свойство, чтобы определить, какое растровое изображение будет отображаться в качестве значка узла проекта.  
  
## <a name="testing-the-custom-project-node-icon"></a>Тестирование значка узла пользовательского проекта  
 Проверьте фабрику проекта, чтобы определить, создает ли она иерархию проектов, в которой находится пользовательский значок проекта.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Проверка значка узла пользовательского проекта  
  
1. Начните отладку и в экспериментальном экземпляре создайте новый Симплепрожект.  
  
2. В созданном проекте Обратите внимание, что SimpleProjectNode.bmp используется в качестве значка узла проекта.  
  
     ![Простой проект Узел нового проекта](../extensibility/media/simpleprojnewprojectnode.png "симплепрожневпрожектноде")  
  
3. Откройте файл Program.cs в редакторе кода. Вы должны увидеть исходный код, похожий на следующий код.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Обратите внимание, что параметры шаблона $nameSpace $ и $className $ не имеют новых значений. Вы узнаете, как реализовать подстановку параметров шаблона в следующем разделе.  
  
## <a name="substituting-template-parameters"></a>Подстановка параметров шаблона  
 В предыдущем разделе вы зарегистрировали шаблон проекта в Visual Studio с помощью `ProvideProjectFactory` атрибута. Таким образом, регистрация пути к папке шаблона позволяет включить базовую подстановку параметров шаблона, переопределив и развернув `ProjectNode.AddFileFromTemplate` класс. Дополнительные сведения см. в разделе о [создании нового проекта: в части 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Теперь добавьте в класс код замены `AddFileFromTemplate` .  
  
#### <a name="to-substitute-template-parameters"></a>Замена параметров шаблона  
  
1. Добавьте в файл SimpleProjectNode.cs следующую `using` инструкцию.  
  
   ```  
   using System.IO;  
   ```  
  
2. Замените `AddFileFromTemplate` метод, используя следующий код.  
  
   ```  
   public override void AddFileFromTemplate(  
       string source, string target)  
   {  
       string nameSpace =   
           this.FileTemplateProcessor.GetFileNamespace(target, this);  
       string className = Path.GetFileNameWithoutExtension(target);  
  
       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
       this.FileTemplateProcessor.AddReplace("$className$", className);  
  
       this.FileTemplateProcessor.UntokenFile(source, target);  
       this.FileTemplateProcessor.Reset();  
   }  
   ```  
  
3. Установите точку останова в методе сразу после `className` оператора присваивания.  
  
   Операторы присваивания определяют разумные значения для пространства имен и имя нового класса. Два `ProjectNode.FileTemplateProcessor.AddReplace` вызова метода заменяют соответствующие значения параметров шаблона, используя эти новые значения.  
  
## <a name="testing-the-template-parameter-substitution"></a>Проверка подстановки параметра шаблона  
 Теперь можно проверить подстановку параметров шаблона.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Проверка подстановки параметра шаблона  
  
1. Начните отладку и в экспериментальном экземпляре создайте новый Симплепрожект.  
  
2. Выполнение останавливается в точке останова в `AddFileFromTemplate` методе.  
  
3. Проверьте значения `nameSpace` `className` параметров и.  
  
   - `nameSpace` Получает значение \<RootNamespace> элемента в файле шаблона проекта \темплатес\прожектс\симплепрожект\симплепрожект.мипрож. В этом случае значение равно «Мирутнамеспаце».  
  
   - `className` присваивается значение имени исходного файла класса без расширения имени файла. В этом случае первый файл, который необходимо скопировать в папку назначения, — AssemblyInfo.cs; Таким образом, значение className — «AssemblyInfo».  
  
4. Удалите точку останова и нажмите клавишу F5, чтобы продолжить выполнение.  
  
    Visual Studio должен завершить создание проекта.  
  
5. Откройте файл Program.cs в редакторе кода. Вы должны увидеть исходный код, похожий на следующий код.  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Linq;  
   using System.Text;  
  
   namespace MyRootNamespace  
   {  
       public class Program  
       {  
           static void Main(string[] args)  
           {  
               Console.WriteLine("Hello VSX!!!");  
               Console.ReadKey();  
           }  
       }  
   }  
   ```  
  
    Обратите внимание, что пространство имен теперь имеет значение "Мирутнамеспаце", а имя класса теперь — "Program".  
  
6. Начните отладку проекта. Новый проект должен компилироваться, запускаться и отображать "Hello VSX!!!". в окне консоли.  
  
    ![Команда Simple Project](../extensibility/media/simpleprojcommand.png "симплепрожкомманд")  
  
   Поздравляем! Вы реализовали базовую управляемую систему проектов.
