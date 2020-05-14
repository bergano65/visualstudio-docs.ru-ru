---
title: Создание базовой системы проекта, часть 1 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739720"
---
# <a name="create-a-basic-project-system-part-1"></a>Создание базовой проектной системы, часть 1
В Visual Studio проекты — это контейнеры, которые разработчики используют для организации файлов исходного кода и других ресурсов. Проекты отображаются как дети решений в **Solution Explorer.** Проекты позволяют организовывать, создавать, отлаживать и развертывать исходный код и создавать ссылки на web-службы, базы данных и другие ресурсы.

 Проекты определяются в файлах проекта, например в файле *.csproj* для проекта Visual C. Вы можете создать свой собственный тип проекта, который имеет свое собственное расширение названия файла проекта. Для получения дополнительной информации [Project types](../extensibility/internals/project-types.md)о типах проектов см.

> [!NOTE]
> Если вам нужно расширить Visual Studio с пользовательским типом проекта, мы настоятельно рекомендуем использовать [систему проектов Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS), которая имеет ряд преимуществ по сравнению с созданием проектной системы с нуля:
>
> - Легче на посадке.  Даже базовая проектная система требует десятков тысяч строк кода.  Использование VSPS снижает стоимость посадки до нескольких кликов, прежде чем вы будете готовы настроить его под ваши нужды.
> - Упрощенное техническое обслуживание.  Используя VSPS, вам нужно только поддерживать свои собственные сценарии.  Мы занимаемся содержанием всей инфраструктуры проектной системы.
>
>   Если вам нужно таргетировать версии Visual Studio старше Visual Studio 2013, вы не сможете использовать VSPS в расширении Visual Studio.  Если это так, это пошаговая прогулка является хорошим местом, чтобы начать работу.

 Это пошаговое решение показывает, как создать тип проекта с расширением названия файла проекта *.myproj.* Это пошаговое решение заимствовано из существующей системы проектов Visual C.

> [!NOTE]
> Для получения дополнительных примеров проектов расширения [см.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

 Это пошаговое промывое учит, как выполнить эти задачи:

- Создайте базовый тип проекта.

- Создайте базовый шаблон проекта.

- Зарегистрируйте шаблон проекта в Visual Studio.

- Создайте экземпляр проекта, открыв поле диалога **Нового проекта,** а затем с помощью шаблона.

- Создайте проектную фабрику для проектной системы.

- Создайте узла проекта для проектной системы.

- Добавьте пользовательские значки для проектной системы.

- Реализация замены параметров базового шаблона.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

 Необходимо также загрузить исходный код для [рамочной программы управляемого пакета для проектов.](https://github.com/tunnelvisionlabs/MPFProj10) Извлеките файл в место, доступное для решения, которое вы собираетесь создать.

## <a name="create-a-basic-project-type"></a>Создание базового типа проекта
 Создайте проект СЗ VSIX под названием **SimpleProject**. (**Файл** > **новый** > **проект,** а затем **Visual C е** > **Расширяемый** > **VSIX проекта**). Добавить шаблон элемента проекта Visual Studio Package (на **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**, а затем перейдите к **Расширяемый** > **Visual Studio Package).** Назовите файл *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Создание базового шаблона проекта
 Теперь вы можете изменить этот базовый VSPackage для реализации нового типа проекта *.myproj.* Чтобы создать проект, основанный на типе проекта *.myproj,* Visual Studio должна знать, какие файлы, ресурсы и ссылки следует добавить в новый проект. Чтобы предоставить эту информацию, поместите файлы проекта в папку шаблона проекта. Когда пользователь использует проект *.myproj* для создания проекта, файлы копируются в новый проект.

### <a name="to-create-a-basic-project-template"></a>Создание базового шаблона проекта

1. Добавьте в проект три папки, одна под другой: *Шаблоны (Проекты) Простой Проект*. (В **Solution Explorer**, правой кнопкой мыши узла проекта **SimpleProject,** укажите, чтобы **добавить,** а затем нажмите New **Folder**. Назовите папку *шаблонов*. В папке *шаблонов* добавьте папку с именем *«Проекты».* В папке *«Проекты»* добавьте папку под названием *SimpleProject*.)

2. В папке *«Шаблоны»Проекты и SimpleProject* добавьте файл изображения Bitmap для использования в качестве значка под названием *SimpleProject.ico*. При нажатии **На кнопку Добавить,** редактор значок открывается.

3. Сделайте икону отличительной. Эта иконка появится в диалоговом окне **нового проекта** позже в пошаговом шаге.

    ![Значок: значок простого проекта](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Сохранить значок и закрыть редактор значка.

5. В папку *«Шаблоны»Проекты и SimpleProject* добавьте элемент **класса** под названием *Program.cs*.

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
   > Это не окончательная форма *Program.cs* кода; параметры замены будут рассмотрены на более позднем этапе. Вы можете видеть ошибки компиляции, но до тех пор, как **файл BuildAction** является **содержание,** вы должны быть в состоянии построить и запустить проект в обычном режиме.

7. Сохраните файл.

8. Копируйте *AssemblyInfo.cs* файл из папки *«Свойства»* в папку *Project'SimpleProject.*

9. В папку *Projects'SimpleProject* добавить файл XML под названием *SimpleProject.myproj*.

   > [!NOTE]
   > Расширение названия файла для всех проектов этого типа *.myproj*. Если вы хотите изменить его, вы должны изменить его везде, он упоминается в пошаговом пошаговом уходе.

10. Замените существующее содержимое следующими строками.

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

12. В окне **Свойства,** установить **действий сборки** *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico*, и *SimpleProject.myproj* к **содержимому**, и установить их **Включить в свойства VSIX** **True**.

    Этот шаблон проекта описывает базовый проект Visual C, который имеет как конфигурацию Debug, так и конфигурацию release. Проект включает в себя два исходных файла, *AssemblyInfo.cs* и *Program.cs,* а также несколько ссылок на сборку. Когда проект создается из шаблона, значение ProjectGuid автоматически заменяется новым GUID.

    В **Solution Explorer**расширенная папка **шаблонов** должна отображаться следующим образом:

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
 Вы должны сообщить Visual Studio о местонахождении папки шаблона проекта. Для этого добавьте атрибут в класс VSPackage, который реализует фабрику проекта, чтобы местоположение шаблона было записано в системный реестр при построении VSPackage. Начните с создания базовой фабрики проектов, которая определяется заводом проекта GUID. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> атрибут для подключения фабрики проекта к классу. `SimpleProjectPackage`

### <a name="to-create-a-basic-project-factory"></a>Создание базовой фабрики проектов

1. Создайте GUID для вашей фабрики проектов (в меню **«Инструменты»,** нажмите **«Создайте GUID»** или воспользуйтесь в следующем примере. Добавьте GUID в `SimpleProjectPackage` класс рядом с `PackageGuidString`разделом с уже определенным . GUIDs должны быть как в форме GUID и строки. Полученный код должен напоминать следующий пример.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Добавьте класс в верхнюю папку *SimpleProject* под названием *SimpleProjectFactory.cs.*

3. Добавьте следующие директивы using.

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Добавьте атрибут GUID `SimpleProjectFactory` в класс. Ценность атрибута - новый проект завода GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Теперь вы можете зарегистрировать шаблон проекта.

### <a name="to-register-the-project-template"></a>Регистрация шаблона проекта

1. В *SimpleProjectPackage.cs,* <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> добавить `SimpleProjectPackage` атрибут в класс, следующим образом.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Перестроить решение и убедиться, что он строится без ошибок.

    Восстановление регистрирует шаблон проекта.

   Параметры `defaultProjectExtension` и `possibleProjectExtensions` устанавливаются на расширение названия файла проекта *(.myproj*). Параметр `projectTemplatesDirectory` устанавливается в относительном пути папки *шаблонов.* Во время сборки этот путь будет преобразован в полную сборку и добавлен в реестр для регистрации проектной системы.

## <a name="test-the-template-registration"></a>Проверьте регистрацию шаблонов
 Регистрация шаблонов сообщает Visual Studio о местонахождении папки шаблона проекта, чтобы Visual Studio мог отображать имя шаблона и значок в диалоговом окне **нового проекта.**

### <a name="to-test-the-template-registration"></a>Проверить регистрацию шаблона

1. Нажмите **F5,** чтобы начать отладку экспериментального экземпляра Visual Studio.

2. В экспериментальном примере создайте новый проект нового типа проекта. В диалоговом окне **нового проекта** вы должны увидеть **SimpleProject** под **установленными шаблонами.**

   Теперь у вас есть проектная фабрика, которая зарегистрирована. Тем не менее, он пока не может создать проект. Пакет проекта и фабрика проекта работают вместе, чтобы создать и инициализировать проект.

## <a name="add-the-managed-package-framework-code"></a>Добавление рамочного кода управляемого пакета
 Реализация связи между пакетом проекта и фабрикой проекта.

- Импортируйте файлы исходного кода для рамочной программы управляемого пакета.

    1. Выгрузите проект SimpleProject (в **Solution Explorer,** выберите узла проекта и в контекстном меню нажмите **Unload Project.)** и откройте файл проекта в редакторе XML.

    2. Добавьте следующие блоки в файл \<проекта (чуть выше блоков импорта>). Установите `ProjectBasePath` расположение файла *ProjectBase.files* в только что загруженном вами рамочном коде Управляемого пакета. Возможно, вам придется добавить backslash к названию пути. В противном случае проект может не найти исходный код Рамочной программы управляемого пакета.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Не забудьте backslash в конце пути.

    3. Перезагрузите проект.

    4. Добавьте ссылки на следующие сборки:

        - `Microsoft.VisualStudio.Designer.Interfaces`(в * \<установке VSSDK>»VisualStudioИнтеграция»-Общие сборки»v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Для инициализации проектной фабрики

1. В *файле SimpleProjectPackage.cs* добавьте следующую `using` директиву.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Выизвените `SimpleProjectPackage` класс из `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Зарегистрируйте проектную фабрику. Добавьте следующую `SimpleProjectPackage.Initialize` строку к `base.Initialize`методу, сразу после .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Реализация абстрактного свойства: `ProductUserContext`

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. В *SimpleProjectFactory.cs,* добавьте `using` следующую `using` директиву после существующих директив.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Выизвените `SimpleProjectFactory` класс из `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Добавьте в `SimpleProjectFactory` класс следующий метод фиктивного. Этот метод будет реализован в более позднем разделе.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Добавьте в `SimpleProjectFactory` класс следующее поле и конструктор. Эта `SimpleProjectPackage` ссылка кэшируется в частном поле, так что она может быть использована при настройке сайта поставщика услуг.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Перестроить решение и убедиться, что он строится без ошибок.

## <a name="test-the-project-factory-implementation"></a>Проверьте реализацию проекта на фабрике
 Проверьте, называется ли конструктор для реализации проекта на фабрике.

### <a name="to-test-the-project-factory-implementation"></a>Проверить реализацию проекта завода

1. В *SimpleProjectFactory.cs* файле установите точку разрыва `SimpleProjectFactory` на следующей строке в конструкторе.

    ```csharp
    this.package = package;
    ```

2. Нажмите **F5,** чтобы начать экспериментальный экземпляр Visual Studio.

3. В экспериментальном примере начните создавать новый проект. В диалоговом окне **нового проекта** выберите тип проекта **SimpleProject,** а затем нажмите **OK**. Выполнение прекратится в точке останова.

4. Очистите точку разрыва и прекратите отладку. Поскольку мы еще не создали узел проекта, код создания проекта по-прежнему выбрасывает исключения.

## <a name="extend-the-projectnode-class"></a>Расширить класс ProjectNode
 Теперь можно `SimpleProjectNode` реализовать класс, который `ProjectNode` вытекает из класса. Базовый `ProjectNode` класс выполняет следующие задачи по созданию проекта:

- Копирует файл шаблона проекта, *SimpleProject.myproj*, в новую папку проекта. Копия переименована в соответствии с именем, ввоженным в диалоговую коробку **Нового проекта.** Стоимость `ProjectGuid` недвижимости заменяется новым GUID.

- Пересекает элементы MSBuild файла шаблона проекта, *SimpleProject.myproj*и ищет `Compile` элементы. Для `Compile` каждого целевого файла копируется файл в новую папку проекта.

  Полученный `SimpleProjectNode` класс обрабатывает следующие задачи:

- Позволяет создавать или отбирать значки для проектных и файловых узлов в **Solution Explorer.**

- Позволяет указать дополнительные замены параметров шаблона проекта.

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

   Эта `SimpleProjectNode` реализация класса имеет эти переопределенные методы:

- `ProjectGuid`, который возвращает проект завода GUID.

- `ProjectType`, который возвращает локализованное название типа проекта.

- `AddFileFromTemplate`, который копирует выбранные файлы из папки шаблона в проект назначения. Этот метод дополнительно реализован в более позднем разделе.

  Конструктор, `SimpleProjectNode` как и `SimpleProjectFactory` конструктор, кэширует ссылку `SimpleProjectPackage` в частном поле для последующего использования.

  Чтобы подключить `SimpleProjectFactory` класс `SimpleProjectNode` к классу, необходимо мгновенно `SimpleProjectNode` выполнить `SimpleProjectFactory.CreateProject` новый метод и кэшировать его в частном поле для последующего использования.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Для подключения класса завода проекта и класса узлов

1. В *файле SimpleProjectFactory.cs* добавьте следующую `using` директиву:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Замените `SimpleProjectFactory.CreateProject` метод, используя следующий код.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Перестроить решение и убедиться, что он строится без ошибок.

## <a name="test-the-projectnode-class"></a>Протестировать класс ProjectNode
 Проверьте фабрику проектов, чтобы увидеть, создает ли она иерархию проектов.

### <a name="to-test-the-projectnode-class"></a>Для тестирования класса ProjectNode

1. Нажмите клавишу **F5**, чтобы запустить отладку. В экспериментальном примере создайте новый SimpleProject.

2. Visual Studio должна позвонить на фабрику проектов, чтобы создать проект.

3. Закройте экспериментальный экземпляр Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Добавление пользовательского значка узла проекта
 Значок узла проекта в предыдущем разделе является значком по умолчанию. Вы можете изменить его на пользовательский значок.

### <a name="to-add-a-custom-project-node-icon"></a>Добавление пользовательского значка узла проекта

1. В папку **Ресурсов** добавьте файл bitmap под названием *SimpleProjectNode.bmp.*

2. В окнах **Properties** уменьшите бит-карту до 16 на 16 пикселей. Сделайте бит-карту отличительной.

    ![Команда простого проекта](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. В окне **Свойств** измените **действие сборки** битовой карты на **встроенный ресурс.**

4. В *SimpleProjectNode.cs*добавьте `using` следующие директивы:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Добавьте в `SimpleProjectNode` класс следующее статическое поле и конструктор.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Добавьте следующее свойство `SimpleProjectNode` в начало класса.

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

   Во время `SimpleProjectNode` статического строительства, извлекает бит-карту узла проекта из сборки манифест ресурсов и кэширует его в частном поле для последующего использования. Обратите внимание на <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> синтаксис пути изображения. Чтобы увидеть имена ресурсов, встроенных в сборку, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> используйте метод. Когда этот метод применяется к сборке, `SimpleProject` результаты должны быть следующими:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Ресурс.SimpleProjectNode.bmp*

  Во время строительства экземпляра базовый `ProjectNode` класс загружает *Resources.imagelis.bmp,* в которые встроены обычно используемые 16 х 16 бит-карт от *Resources'imagelis.bmp.* Этот список bitmap `SimpleProjectNode` сделан `ImageHandler.ImageList`имеющимся к как . `SimpleProjectNode`прививает в список битную карту узла проекта. Смещение битовой карты узла проекта в списке изображений кэшируется для последующего использования в качестве значения государственного `ImageIndex` имущества. Visual Studio использует это свойство, чтобы определить, какую бит-карту для отображения в качестве значка узла проекта.

## <a name="test-the-custom-project-node-icon"></a>Проверьте пользовательский значок узла проекта
 Проверьте фабрику проекта, чтобы увидеть, создает ли она иерархию проектов с пользовательским значком узла проекта.

### <a name="to-test-the-custom-project-node-icon"></a>Для проверки пользовательского значка узла проекта

1. Начать отладку, а в экспериментальном примере создать новый SimpleProject.

2. В недавно созданном проекте обратите внимание, что *SimpleProjectNode.bmp* используется в качестве значка узла проекта.

     ![Простой проект Узел нового проекта](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Откройте файл *Program.cs* в редакторе кода. Вы должны увидеть исходный код, напоминающий следующий код.

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

     Обратите внимание, что параметры шаблона $nameSpace$ и $className$ не имеют новых значений. Вы узнаете, как реализовать замену параметров шаблона в следующем разделе.

## <a name="substitute-template-parameters"></a>Параметры шаблона замены
 В предыдущем разделе вы зарегистрировали шаблон проекта с `ProvideProjectFactory` помощью Visual Studio с помощью атрибута. Регистрация пути папки шаблона таким образом позволяет включить замену параметров базового шаблона, переопределяя и расширяя `ProjectNode.AddFileFromTemplate` класс. Для получения дополнительной информации, [см.](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Теперь добавьте `AddFileFromTemplate` код замены в класс.

### <a name="to-substitute-template-parameters"></a>Замена параметров шаблона

1. В *SimpleProjectNode.cs* файле добавьте следующую `using` директиву.

   ```csharp
   using System.IO;
   ```

2. Замените `AddFileFromTemplate` метод, используя следующий код.

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

3. Установите точку разрыва в методе сразу после оператора `className` назначения.

   Операторы назначения определяют разумные значения для пространства имен и нового имени класса. Два `ProjectNode.FileTemplateProcessor.AddReplace` вызова метода заменяют соответствующие значения параметров шаблона, используя эти новые значения.

## <a name="test-the-template-parameter-substitution"></a>Проверьте замену параметра шаблона
 Теперь вы можете протестировать замену параметров шаблона.

### <a name="to-test-the-template-parameter-substitution"></a>Проверить замену параметра шаблона

1. Начать отладку, а в экспериментальном примере создать новый SimpleProject.

2. Выполнение останавливается в точке разрыва в методе. `AddFileFromTemplate`

3. Изучите значения `nameSpace` для `className` параметров.

   - `nameSpace`придается значение \<RootNamespace> элементом в файле шаблона проекта *«Шаблоны»Проекты »SimpleProject»SimpleProject.myproj* project. В этом случае используется значение `MyRootNamespace`.

   - `className`дается значение имени исходного файла класса без расширения имени файла. В этом случае первый файл, который будет скопирован в папку *назначения, AssemblyInfo.cs;* таким образом, значение ClassName . `AssemblyInfo`

4. Удалите точку разрыва и нажмите **F5,** чтобы продолжить выполнение.

    Visual Studio должна закончить создание проекта.

5. Откройте файл *Program.cs* в редакторе кода. Вы должны увидеть исходный код, напоминающий следующий код.

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

    Обратите внимание, что `MyRootNamespace` пространство имен теперь `Program`и имя класса теперь .

6. Начните отладку проекта. Новый проект должен компилировать, запускать и отображать "Hello VSX!!!" в окне консоли.

    ![Команда Simple Project](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Поздравляем! Вы внедрили базовую управляемую систему проекта.
