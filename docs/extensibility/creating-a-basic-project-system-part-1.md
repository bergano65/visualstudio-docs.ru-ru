---
title: Создание базовой системы проектов, часть 1 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73bacf2c5d1650da91093c92c67e6b67bbbc73a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633506"
---
# <a name="create-a-basic-project-system-part-1"></a>Создание базовой системы проектов, часть 1
В Visual Studio проекты — это контейнеры, используемые разработчиками для организации файлов исходного кода и других ресурсов. Проекты отображаются как дочерние элементы решений в **Обозреватель решений**. Проекты позволяют упорядочивать, собирать, отлаживать и развертывать исходный код и создавать ссылки на веб-службы, базы данных и другие ресурсы.

 Проекты определяются в файлах проекта, например *CSPROJ* -файл для визуального C# проекта. Можно создать собственный тип проекта с расширением имени файла проекта. Дополнительные сведения о типах проектов см. в разделе [типы проектов](../extensibility/internals/project-types.md).

> [!NOTE]
> Если необходимо расширить Visual Studio с помощью пользовательского типа проекта, мы настоятельно рекомендуем использовать [систему проектов Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS), имеющую ряд преимуществ по сравнению с созданием системы проектов с нуля.
>
> - Упрощение адаптации.  Даже для базовой системы проектов требуется десятка тысяч строк кода.  Использование подсчета позволяет снизить затраты на адаптации до нескольких щелчков, прежде чем вы сможете настроить его в своих нуждах.
> - Более простое обслуживание.  Используя VSPS, необходимо поддерживать только собственные сценарии.  Мы работаем над отработкой всей инфраструктуры системы проектов.
>
>   Если вам нужно использовать версии Visual Studio более ранние, чем Visual Studio 2013, вы не сможете воспользоваться VSPS в расширении Visual Studio.  Если это так, это пошаговое руководство является хорошим местом для начала работы.

 В этом пошаговом руководстве показано, как создать тип проекта с расширением имени файла проекта *. мипрож*. Это пошаговое руководство позаимствовано C# из существующей системы визуальных проектов.

> [!NOTE]
> Дополнительные примеры проектов расширений см. в разделе [VSSDK Samples](https://aka.ms/vs2015sdksamples).

 В этом пошаговом руководстве объясняется, как выполнить эти задачи:

- Создайте базовый тип проекта.

- Создайте базовый шаблон проекта.

- Зарегистрируйте шаблон проекта в Visual Studio.

- Создайте экземпляр проекта, открыв диалоговое окно **Создание проекта** , а затем используя шаблон.

- Создание фабрики проектов для системы проектов.

- Создайте узел проекта для системы проектов.

- Добавление пользовательских значков для системы проектов.

- Реализуйте базовую подстановку параметров шаблона.

## <a name="prerequisites"></a>Необходимые компоненты
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

 Также необходимо загрузить исходный код для [платформы управляемого пакета для проектов](https://github.com/tunnelvisionlabs/MPFProj10). Извлеките файл в расположение, доступное для решения, которое вы собираетесь создать.

## <a name="create-a-basic-project-type"></a>Создание базового типа проекта
 Создайте проект C# VSIX с именем **симплепрожект**. (**Файл**  > **Новый**  > **проект** , а затем**расширяемость** **Visual C#**   >   > **проекта VSIX**). Добавьте шаблон элемента проекта пакета Visual Studio (на **Обозреватель решений**щелкните правой кнопкой мыши узел проекта и выберите **Добавить**  > **новый элемент**, затем перейдите в раздел **расширяемость**  > **пакет Visual Studio**). Назовите файл *симплепрожектпаккаже*.

## <a name="creating-a-basic-project-template"></a>Создание базового шаблона проекта
 Теперь можно изменить этот базовый пакет VSPackage, чтобы реализовать новый тип проекта *. мипрож* . Чтобы создать проект, основанный на типе проекта *. мипрож* , Visual Studio необходимо выяснить, какие файлы, ресурсы и ссылки нужно добавить в новый проект. Чтобы предоставить эти сведения, помещайте файлы проекта в папку шаблона проекта. Когда пользователь использует проект *мипрож* для создания проекта, файлы копируются в новый проект.

### <a name="to-create-a-basic-project-template"></a>Создание базового шаблона проекта

1. Добавьте в проект три папки — один из следующих: *темплатес\прожектс\симплепрожект*. (В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта **симплепрожект** , наведите указатель на пункт **добавить**и выберите пункт **создать папку**. Назовите *шаблоны*папок. В папке *Templates* добавьте папку с именем *Projects*. В папке *проекты* добавьте папку с именем *симплепрожект*.)

2. В папке *темплатес\прожектс\симплепрожект* добавьте файл точечного рисунка для использования в качестве значка с именем *симплепрожект. ico*. При нажатии кнопки **Добавить**открывается Редактор значков.

3. Сделайте значок отличительным. Этот значок будет отображаться в диалоговом окне " **Новый проект** " Далее в этом пошаговом руководстве.

    ![Значок простого проекта](../extensibility/media/simpleprojicon.png "симплепрожикон")

4. Сохраните значок и закройте редактор значков.

5. В папке *темплатес\прожектс\симплепрожект* добавьте элемент **класса** с именем *Program.CS*.

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
   > Это не последняя форма кода *Program.CS* ; параметры замены будут обрабатываться на более позднем этапе. Вы можете увидеть ошибки компиляции, но при условии, что содержимое **файла** является **содержимым**, вы сможете создать и запустить проект обычным образом.

7. Сохраните файл.

8. Скопируйте файл *AssemblyInfo.CS* из папки *Properties* в папку *прожектс\симплепрожект* .

9. В папке *прожектс\симплепрожект* добавьте XML-файл с именем *симплепрожект. мипрож*.

   > [!NOTE]
   > Расширение имени файла для всех проектов этого типа — *. мипрож*. Если вы хотите изменить его, его необходимо изменить везде, где он упоминается в этом пошаговом руководстве.

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

12. В окне **Свойства** задайте для **действия сборки** *AssemblyInfo.CS*, *Program.CS*, *симплепрожект. ico*и *СИМПЛЕПРОЖЕКТ. мипрож* значение **Content**и задайте их свойства **include в VSIX** . в **значение true**.

    Этот шаблон проекта описывает базовый проект Visual C# с конфигурацией отладки и конфигурацией выпуска. Проект включает два исходных файла, *AssemblyInfo.CS* и *Program.CS*, и несколько ссылок на сборки. При создании проекта на основе шаблона значение Прожектгуид автоматически заменяется новым идентификатором GUID.

    В **Обозреватель решений**Расширенная папка **Templates** должна выглядеть следующим образом:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Создание базовой фабрики проектов
 Необходимо сообщить Visual Studio о расположении папки шаблона проекта. Для этого добавьте атрибут в класс VSPackage, реализующий фабрику проектов, чтобы расположение шаблона записывалось в системный реестр при построении VSPackage. Начните с создания базовой фабрики проектов, определяемой идентификатором GUID фабрики проектов. Используйте атрибут <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute>, чтобы подключить фабрику проектов к `SimpleProjectPackage` классу.

### <a name="to-create-a-basic-project-factory"></a>Создание базовой фабрики проектов

1. Создайте идентификаторы GUID для фабрики проектов (в меню **Сервис** выберите пункт **Создать GUID**) или используйте его в следующем примере. Добавьте идентификаторы GUID в класс `SimpleProjectPackage` рядом с разделом с уже определенным `PackageGuidString`. Идентификаторы GUID должны быть в форме идентификатора GUID и в форме строки. Результирующий код должен выглядеть следующим образом.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Добавьте класс в верхнюю папку *симплепрожект* с именем *SimpleProjectFactory.CS*.

3. Добавьте следующие директивы using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Добавьте атрибут GUID в класс `SimpleProjectFactory`. Значением атрибута является новый идентификатор GUID фабрики проекта.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Теперь можно зарегистрировать шаблон проекта.

### <a name="to-register-the-project-template"></a>Регистрация шаблона проекта

1. В *SimpleProjectPackage.CS*добавьте атрибут <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> в класс `SimpleProjectPackage`, как показано ниже.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Перестройте решение и убедитесь, что сборка выполняется без ошибок.

    Перестроение регистрирует шаблон проекта.

   Для параметров `defaultProjectExtension` и `possibleProjectExtensions` задано расширение имени файла проекта ( *. мипрож*). Параметр `projectTemplatesDirectory` задает относительный путь к папке *Templates* . Во время сборки этот путь будет преобразован в полную сборку и добавлен в реестр для регистрации системы проектов.

## <a name="test-the-template-registration"></a>Тестирование регистрации шаблона
 Регистрация шаблона сообщает Visual Studio о расположении папки шаблонов проектов, чтобы Visual Studio могла отображать имя и значок шаблона в диалоговом окне **Новый проект** .

### <a name="to-test-the-template-registration"></a>Проверка регистрации шаблона

1. Нажмите клавишу **F5** , чтобы начать отладку экспериментального экземпляра Visual Studio.

2. В экспериментальном экземпляре создайте новый проект созданного типа проекта. В диалоговом окне **Новый проект** в разделе **Установленные шаблоны**должно отобразиться **симплепрожект** .

   Теперь у вас есть зарегистрированная фабрика проектов. Однако он еще не может создать проект. Пакет проекта и фабрика проектов работают вместе для создания и инициализации проекта.

## <a name="add-the-managed-package-framework-code"></a>Добавление кода платформы управляемого пакета
 Реализуйте соединение между пакетом проекта и фабрикой проекта.

- Импортируйте файлы исходного кода для платформы управляемого пакета.

    1. Выгрузите проект Симплепрожект (в **Обозреватель решений**выберите узел проекта и в контекстном меню выберите команду **Выгрузить проект**) и откройте файл проекта в редакторе XML.

    2. Добавьте следующие блоки в файл проекта (непосредственно над блоками > \<Import). Задайте для `ProjectBasePath` расположение файла *прожектбасе. Files* в только что загруженном коде платформы управляемого пакета. Может потребоваться добавить в путь обратную косую черту. В противном случае проект может не найти исходный код платформы управляемого пакета.

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

        - `Microsoft.VisualStudio.Designer.Interfaces` (в *\<VSSDK install > \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Инициализация фабрики проектов

1. В файле *SimpleProjectPackage.CS* добавьте следующую директиву `using`.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Создайте производный класс `SimpleProjectPackage` от `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Зарегистрируйте фабрику проекта. Добавьте следующую строку в метод `SimpleProjectPackage.Initialize` сразу после `base.Initialize`.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Реализуйте `ProductUserContext` абстрактного свойства:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. В *SimpleProjectFactory.CS*добавьте следующую директиву `using` после существующих директив `using`.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Создайте производный класс `SimpleProjectFactory` от `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Добавьте следующий фиктивный метод в класс `SimpleProjectFactory`. Этот метод будет реализован в следующем разделе.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Добавьте в класс `SimpleProjectFactory` следующее поле и конструктор. Ссылка на эту `SimpleProjectPackage` кэшируется в частном поле, чтобы его можно было использовать при настройке сайта поставщика услуг.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Перестройте решение и убедитесь, что сборка выполняется без ошибок.

## <a name="test-the-project-factory-implementation"></a>Тестирование реализации фабрики проектов
 Проверьте, вызывается ли конструктор для реализации фабрики проектов.

### <a name="to-test-the-project-factory-implementation"></a>Тестирование реализации фабрики проектов

1. В файле *SimpleProjectFactory.CS* установите точку останова в следующей строке конструктора `SimpleProjectFactory`.

    ```csharp
    this.package = package;
    ```

2. Нажмите клавишу **F5** , чтобы запустить экспериментальный экземпляр Visual Studio.

3. В экспериментальном экземпляре начните создавать новый проект. В диалоговом окне **Новый проект** выберите тип проекта **симплепрожект** и нажмите кнопку **ОК**. Выполнение прекратится в точке останова.

4. Очистите точку останова и отключите отладку. Так как мы еще не создали узел проекта, код создания проекта по-прежнему создает исключения.

## <a name="extend-the-projectnode-class"></a>Расширение класса ProjectNode
 Теперь можно реализовать класс `SimpleProjectNode`, производный от класса `ProjectNode`. Базовый класс `ProjectNode` обрабатывает следующие задачи создания проекта:

- Копирует файл шаблона проекта *симплепрожект. мипрож*в папку нового проекта. Копия переименовывается в соответствии с именем, введенным в диалоговом окне **Новый проект** . Значение свойства `ProjectGuid` заменяется новым идентификатором GUID.

- Обходят элементы MSBuild файла шаблона проекта *симплепрожект. мипрож*и ищет элементы `Compile`. Для каждого `Compile` целевого файла копирует файл в папку нового проекта.

  Производный класс `SimpleProjectNode` обрабатывает следующие задачи:

- Включает создание или выбор значков для узлов проектов и файлов в **Обозреватель решений** .

- Включает возможность указания дополнительных подстановок параметров шаблона проекта.

### <a name="to-extend-the-projectnode-class"></a>Расширение класса ProjectNode

1. Добавьте класс с именем `SimpleProjectNode.cs`.

2. Замените существующий код следующим кодом:

   ```csharp
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
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
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

   Эта `SimpleProjectNode` реализация класса имеет следующие переопределенные методы:

- `ProjectGuid`, возвращающий идентификатор GUID фабрики проекта.

- `ProjectType`, возвращающее локализованное имя типа проекта.

- `AddFileFromTemplate`, который копирует выбранные файлы из папки шаблонов в целевой проект. Этот метод далее реализован в следующем разделе.

  Конструктор `SimpleProjectNode`, как и конструктор `SimpleProjectFactory`, кэширует `SimpleProjectPackage` ссылку в частном поле для последующего использования.

  Чтобы подключить класс `SimpleProjectFactory` к классу `SimpleProjectNode`, необходимо создать экземпляр нового `SimpleProjectNode` в методе `SimpleProjectFactory.CreateProject` и кэшировать его в частном поле для последующего использования.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Подключение класса фабрики проектов и класса Node

1. В файл *SimpleProjectFactory.CS* добавьте следующую директиву `using`:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Замените метод `SimpleProjectFactory.CreateProject` с помощью следующего кода.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Перестройте решение и убедитесь, что сборка выполняется без ошибок.

## <a name="test-the-projectnode-class"></a>Тестирование класса ProjectNode
 Проверьте фабрику проекта, чтобы определить, создает ли она иерархию проектов.

### <a name="to-test-the-projectnode-class"></a>Тестирование класса ProjectNode

1. Нажмите клавишу **F5** , чтобы начать отладку. В экспериментальном экземпляре создайте новый Симплепрожект.

2. Visual Studio следует вызывать фабрику проектов для создания проекта.

3. Закройте экспериментальный экземпляр Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Добавить пользовательский значок узла проекта
 Значок узла проекта в предыдущем разделе является значком по умолчанию. Его можно изменить на пользовательский значок.

### <a name="to-add-a-custom-project-node-icon"></a>Добавление пользовательского значка узла проекта

1. В папке **Resources** добавьте файл точечного рисунка с именем *симплепрожектноде. bmp*.

2. В окнах **свойств** Сократите точечный рисунок до 16 пикселов. Сделайте свой точечный рисунок.

    ![Простая проектная фабрика](../extensibility/media/simpleprojprojectcomm.png "симплепрожпрожекткомм")

3. В окне **Свойства** измените **действие сборки** точечного рисунка на **внедренный ресурс**.

4. В *SimpleProjectNode.CS*добавьте следующие директивы `using`:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Добавьте следующее статическое поле и конструктор в класс `SimpleProjectNode`.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Добавьте следующее свойство в начало класса `SimpleProjectNode`.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Замените конструктор экземпляра следующим кодом.

   ```csharp
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

   Во время статической конструкции `SimpleProjectNode` извлекает битовую карту узла проекта из ресурсов манифеста сборки и кэширует ее в частном поле для последующего использования. Обратите внимание на синтаксис пути к образу <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>. Чтобы просмотреть имена ресурсов манифеста, внедренных в сборку, используйте метод <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>. При применении этого метода к `SimpleProject` сборке результаты должны выглядеть следующим образом:

- *Симплепрожект. Resources. Resources*

- *VisualStudio. Project. Resources*

- *Симплепрожект. VSPackage. Resources*

- *Resources. имажелис. bmp*

- *Microsoft. VisualStudio. Project. Донтшовагаиндиалог. Resources*

- *Microsoft. VisualStudio. Project. Секуритиварнингдиалог. Resources*

- *Симплепрожект. Resources. Симплепрожектноде. bmp*

  Во время создания экземпляра `ProjectNode` базовый класс загружает *Resources. имажелис. bmp*, в котором часто используются 16 x 16 точечных рисунков из *ресаурцес\имажелис.БМП*. Этот список точечных рисунков доступен для `SimpleProjectNode` `ImageHandler.ImageList`. `SimpleProjectNode` добавляет в список битовую карту узла проекта. Смещение растрового изображения узла проекта в списке изображений кэшируется для последующего использования в качестве значения свойства public `ImageIndex`. Visual Studio использует это свойство, чтобы определить, какое растровое изображение будет отображаться в качестве значка узла проекта.

## <a name="test-the-custom-project-node-icon"></a>Проверка значка узла пользовательского проекта
 Проверьте фабрику проекта, чтобы определить, создает ли она иерархию проектов, в которой находится пользовательский значок проекта.

### <a name="to-test-the-custom-project-node-icon"></a>Проверка значка узла пользовательского проекта

1. Начните отладку и в экспериментальном экземпляре создайте новый Симплепрожект.

2. В созданном проекте Обратите внимание, что в качестве значка узла проекта используется *симплепрожектноде. bmp* .

     ![Простой проект новый узел проекта](../extensibility/media/simpleprojnewprojectnode.png "симплепрожневпрожектноде")

3. Откройте *Program.CS* в редакторе кода. Вы должны увидеть исходный код, похожий на следующий код.

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

     Обратите внимание, что параметры шаблона $nameSpace $ и $className $ не имеют новых значений. Вы узнаете, как реализовать подстановку параметров шаблона в следующем разделе.

## <a name="substitute-template-parameters"></a>Замена параметров шаблона
 В предыдущем разделе вы зарегистрировали шаблон проекта в Visual Studio с помощью атрибута `ProvideProjectFactory`. Таким образом, регистрация пути к папке шаблона позволяет включить базовую подстановку параметров шаблона, переопределив и развернув класс `ProjectNode.AddFileFromTemplate`. Дополнительные сведения см. в разделе о [создании нового проекта: в части 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Теперь добавьте код замены в класс `AddFileFromTemplate`.

### <a name="to-substitute-template-parameters"></a>Замена параметров шаблона

1. В файле *SimpleProjectNode.CS* добавьте следующую директиву `using`.

   ```csharp
   using System.IO;
   ```

2. Замените метод `AddFileFromTemplate` с помощью следующего кода.

   ```csharp
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

3. Установите точку останова в методе сразу после оператора присваивания `className`.

   Операторы присваивания определяют разумные значения для пространства имен и имя нового класса. Два вызова метода `ProjectNode.FileTemplateProcessor.AddReplace` заменяют соответствующие значения параметров шаблона, используя эти новые значения.

## <a name="test-the-template-parameter-substitution"></a>Проверка подстановки параметра шаблона
 Теперь можно проверить подстановку параметров шаблона.

### <a name="to-test-the-template-parameter-substitution"></a>Проверка подстановки параметра шаблона

1. Начните отладку и в экспериментальном экземпляре создайте новый Симплепрожект.

2. Выполнение останавливается в точке останова в методе `AddFileFromTemplate`.

3. Проверьте значения параметров `nameSpace` и `className`.

   - `nameSpace` получает значение элемента \<RootNamespace > в файле шаблона проекта *\темплатес\прожектс\симплепрожект\симплепрожект.мипрож* . В этом случае используется значение `MyRootNamespace`.

   - `className` присваивается значение имени исходного файла класса без расширения имени файла. В этом случае первый файл, который необходимо скопировать в папку назначения, — *AssemblyInfo.CS*; Таким образом, значение className — `AssemblyInfo`.

4. Удалите точку останова и нажмите клавишу **F5** , чтобы продолжить выполнение.

    Visual Studio должен завершить создание проекта.

5. Откройте *Program.CS* в редакторе кода. Вы должны увидеть исходный код, похожий на следующий код.

   ```csharp
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

    Обратите внимание, что теперь пространство имен `MyRootNamespace`, а имя класса теперь `Program`.

6. Начните отладку проекта. Новый проект должен компилироваться, запускаться и отображать "Hello VSX!!!". в окне консоли.

    ![Команда Simple Project](../extensibility/media/simpleprojcommand.png "симплепрожкомманд")

   Поздравляем! Вы реализовали базовую управляемую систему проектов.
