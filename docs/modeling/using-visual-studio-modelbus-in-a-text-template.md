---
title: С помощью Visual Studio ModelBus в текстовом шаблоне | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0184e3b543e509d0e523504c0ea07f6fcc36775f
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Использование Visual Studio ModelBus в текстовом шаблоне
При написании текстовых шаблонов, которые считывают модель, которая содержит [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus ссылается, может потребоваться разрешить ссылки для доступа к целевой модели. В этом случае необходимо адаптировать текстовых шаблонов и упоминаемой доменного языка (DSL):  
  
-   Доменный язык, который является целевым объектом ссылки должен быть установлен адаптер ModelBus, настроенной для доступа из текстовых шаблонов. Если также DSL доступа из другого кода, изменена конфигурация адаптера требуется в дополнение к стандартной ModelBus адаптера.  
  
     Диспетчер адаптеров должен наследовать от <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> и должен иметь атрибут `[HostSpecific(HostName)]`.  
  
-   Шаблон должен наследовать от <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Если вы хотите прочитать модели DSL, которые не содержат ссылок ModelBus, можно использовать процессоры директив, которые создаются в своих проектах DSL. Дополнительные сведения см. в разделе [доступ к модели из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).  
  
 Дополнительные сведения о текстовых шаблонах см. в разделе [создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Создание адаптера шины модели для доступа из текстовых шаблонов  
 Для разрешения ссылки ModelBus в текстовом шаблоне, целевой DSL должен иметь совместимый адаптер. Выполнение текстовых шаблонов в отдельном домене приложения с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] документов редакторы и таким образом адаптер должен загрузить модель, а не доступ к ним через DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Для создания адаптера ModelBus, совместимый с текстовые шаблоны  
  
1.  Если цель DSL решения не **ModelBusAdapter** проекта, создайте его с помощью мастера расширения Modelbus:  
  
    1.  Загрузите и установите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus расширение, если вы еще не сделали это. Дополнительные сведения см. в разделе [визуализации и моделирования SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Откройте файл определения DSL. Щелкните правой кнопкой мыши область конструктора и выберите **включить Modelbus**.  
  
    3.  В диалоговом окне выберите **я хочу предоставить этот DSL для ModelBus**. Можно выбрать оба параметра, если требуется, чтобы этот DSL для предоставления его моделей и использовать ссылки на другие доменного языка.  
  
    4.  Нажмите кнопку **ОК**. В решение DSL будет добавлен новый проект ModelBusAdapter.  
  
    5.  Нажмите кнопку **преобразовать все шаблоны**.  
  
    6.  Выполните повторную сборку решения.  
  
2.  Если требуется доступ к DSL из текстового шаблона и из другого кода, например команды, дублирование **ModelBusAdapter** проекта:  
  
    1.  В проводнике Windows, скопируйте и вставьте папку, содержащую **ModelBusAdapter.csproj**.  
  
    2.  Переименуйте файл проекта (например, для **T4ModelBusAdapter.csproj**).  
  
    3.  В **обозреватель решений**, щелкните правой кнопкой мыши узел решения, укажите **добавить**, а затем нажмите кнопку **существующий проект**. Найдите новый проект адаптера **T4ModelBusAdapter.csproj**.  
  
    4.  В каждом `*.tt` файла нового проекта изменить пространство имен.  
  
    5.  Щелкните правой кнопкой мыши новый проект в обозревателе решений и выберите пункт Свойства. В редакторе свойств измените имена созданную сборку и пространство имен по умолчанию.  
  
    6.  В проекте DslPackage добавьте ссылку в новый проект адаптера, чтобы она содержала ссылки на оба адаптера.  
  
    7.  В DslPackage\source.extension.tt добавьте строку, которая ссылается на нового проекта адаптера.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Преобразовать все шаблоны** и перестройте решение. Ошибки сборки не должно выполняться.  
  
3.  В новом проекте адаптера добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  В AdapterManager.tt:  
  
    -   Измените объявление AdapterManagerBase, чтобы он наследовался от <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Замените атрибут HostSpecific перед классом AdapterManager, ближе к концу файла. Удалите следующую строку:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Вставьте следующую строку:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Этот атрибут фильтрует набор адаптеров, доступный при потребителя modelbus ищет адаптер.  
  
5.  **Преобразовать все шаблоны** и перестройте решение. Ошибки сборки не должно выполняться.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Написание текстового шаблона, который может разрешить ссылки ModelBus  
 Как правило начинается с шаблоном, считывает данные и создает файлы из «источник» DSL. Этот шаблон используется директива, создаваемого в исходный проект DSL для чтения исходных файлов модели способом, который описан в [доступ к модели из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md). Однако источник DSL содержит ModelBus ссылки на «target» DSL. Таким образом, необходимо включить код шаблона для разрешения ссылки и доступ к конечному объекту DSL. Поэтому необходимо адаптировать шаблона, выполните следующие действия:  
  
-   Измените базовый класс шаблона, <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Включить `hostspecific="true"` в директиве template.  
  
-   Добавьте ссылки на сборки для целевой DSL и его адаптер и позволяющие ModelBus.  
  
-   Директива, которая создается как часть целевой DSL не обязательно.  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let's assume they're all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 При выполнении данного шаблона текста `SourceDsl` директива загружает файл `Sample.source`. Шаблон может обращаться к элементам модели, начиная с `this.ModelRoot`. Код можно использовать классы и свойства, DSL.  
  
 Кроме того шаблон можно разрешить ссылки ModelBus. Если ссылки указывают на целевой модели, директивы сборки позволить коду использовать доменные классы и свойства этой модели DSL.  
  
-   Если не использовать директиву, созданный проект DSL, следует включать следующее.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Используйте `this.ModelBus` для получения доступа к ModelBus.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Пошаговое руководство: Тестирование текстовый шаблон, использующий ModelBus  
 В этом пошаговом руководстве выполните следующие действия.  
  
1.  Создайте две доменного языка. Один DSL *потребителя*, имеет `ModelBusReference` свойство, которое может ссылаться на другие DSL *поставщика*.  
  
2.  Создайте два адаптера ModelBus в поставщике: один для доступа в текстовых шаблонах, другой — для обычного кода.  
  
3.  Создайте экземпляр модели доменных языков в одном проекте экспериментальный.  
  
4.  Свойства домена в одной модели, чтобы она указывала на другой модели.  
  
5.  Написать обработчик двойного щелчка, который открывает модели, который указывает.  
  
6.  Запись текстового шаблона, можно загрузить первой модели, выполните ссылку на другой модели и прочитать другой модели.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Создать доменный язык DSL, доступном для ModelBus  
  
1.  Создайте новое решение DSL. Для этого примера выберите шаблон решения задач потока. Задайте имя языка `MBProvider` и расширение файла на «.provide».  
  
2.  В схема определения DSL, щелкните правой кнопкой мыши пустую область диаграммы, который не расположено в верхней части и нажмите кнопку **включить Modelbus**.  
  
    -   Если вы не видите **включить Modelbus**, необходимо загрузить и установить расширения VMSDK ModelBus. Найти на сайте VMSDK: [визуализации и моделирования SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  В **включить Modelbus** выберите **предоставлять этот DSL для ModelBus**и нажмите кнопку **ОК**.  
  
     Новый проект `ModelBusAdapter`, добавляется в решение.  
  
 Теперь у вас есть доменный язык DSL, осуществляемым при помощи текстовых шаблонов через ModelBus. Можно разрешить ссылки на него в коде команд, обработчиками событий или правила, работающих в AppDomain редактор файла модели. Тем не менее текстовые шаблоны выполняются в отдельном домене приложения и нет доступа к модели, когда она редактируется. Если вы хотите получить доступ к ModelBus ссылки на этот DSL из текстового шаблона, необходимо иметь отдельный ModelBusAdapter.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Для создания ModelBus адаптера, настроенного для текстовых шаблонов  
  
1.  В проводнике Windows скопируйте и вставьте папку, содержащую ModelBusAdapter.csproj.  
  
     Имя папки T4ModelBusAdapter.  
  
     Переименуйте файл проекта T4ModelBusAdapter.csproj.  
  
2.  В обозревателе решений добавьте решение MBProvider T4ModelBusAdapter. Щелкните правой кнопкой мыши узел решения, выберите пункт **добавить**, а затем нажмите кнопку **существующий проект**.  
  
3.  Щелкните правой кнопкой мыши узел проекта T4ModelBusAdapter и выберите пункт Свойства. В окне свойств проекта измените **имя сборки** и **пространство имен по умолчанию** для `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  В каждом файле *.tt в T4ModelBusAdapter вставьте «T4» в последней части этого пространства имен, чтобы строка выглядит следующим образом.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  В `DslPackage` проект, добавить ссылку на проект `T4ModelBusAdapter`.  
  
6.  В DslPackage\source.extension.tt, добавьте следующую строку `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  В `T4ModelBusAdapter` проекта, добавьте ссылку на: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Откройте T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  Измените базовый класс AdapterManagerBase на класс <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Эта часть файла теперь выглядит следующим образом.  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  Ближе к концу файла вставьте следующий дополнительный атрибут перед AdapterManager класса.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Результат будет выглядеть примерно так.  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. Нажмите кнопку **преобразовать все шаблоны** в заголовок обозревателя решений.  
  
10. Выполните повторную сборку решения. Нажмите кнопку F5.  
  
11. Проверьте работоспособность DSL, нажав клавишу F5. В экспериментальном проекте откройте `Sample.provider`. Закройте экспериментальный образец [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 ModelBus ссылки на этот DSL может быть устранена в текстовых шаблонах, а также в обычный код.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Конструктор DSL с ModelBus ссылочного свойства домена  
  
1.  Создание нового DSL с помощью шаблона решения минимальной языка. Имя языка MBConsumer и расширение файла на «.consume».  
  
2.  В проекте DSL добавьте ссылку на сборку MBProvider DSL. Щелкните правой кнопкой мыши `MBConsumer\Dsl\References` и нажмите кнопку **добавить ссылку**. В **Обзор** найдите `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Это позволяет создать код, который использует другие DSL. Если вы хотите создавать ссылки на несколько DSL, также добавьте их.  
  
3.  В схема определения DSL, щелкните правой кнопкой мыши на диаграмме и нажмите кнопку **включить ModelBus**. В диалоговом окне выберите **включить этот DSL использовать ModelBus**.  
  
4.  В классе `ExampleElement`, добавить новое свойство домена `MBR`и в окне свойств установите для него `ModelBusReference`.  
  
5.  Щелкните правой кнопкой мыши свойство домена на диаграмме, а затем нажмите кнопку **ModelBusReference изменить определенные свойства**. В диалоговом окне выберите **элемента модели**.  
  
     Значение фильтра диалогового окна файла.  
  
     `Provider File|*.provide`  
  
     Подстрока после «&#124;» фильтров, в диалоговом окне выбора файла. Можно установить его, чтобы включить все файлы с помощью *.\*  
  
     В **тип элемента модели** введите имена один или несколько доменов классы в поставщике DSL (например, Company.MBProvider.Task). Они могут быть абстрактные классы. Если список не заполнено, пользователь может задать ссылку на любой элемент.  
  
6.  Закройте диалоговое окно и **преобразовать все шаблоны**.  
  
 Вы создали DSL, который может содержать ссылки на элементы в другом DSL.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Создать ModelBus ссылку на другой файл в решении  
  
1.  В решении MBConsumer нажмите CTRL + F5. Экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] открывается в **MBConsumer\Debugging** проекта.  
  
2.  Добавить копию Sample.provide для **MBConsumer\Debugging** проекта. Это необходимо, так как ссылка ModelBus должен ссылаться на файл в том же решении.  
  
    1.  Отладка проекта щелкните правой кнопкой мыши **добавить**, а затем нажмите кнопку **существующий элемент**.  
  
    2.  В **добавить элемент** диалогового окна, задайте для фильтра **все файлы (\*.\*)** .  
  
    3.  Перейдите к `MBProvider\Debugging\Sample.provide` и нажмите кнопку **добавить**.  
  
3.  Откройте `Sample.consume`.  
  
4.  Щелкните одной формы в примере и в окне свойств щелкните **[...]**  в свойстве MBR. В диалоговом окне выберите **Обзор** и выберите `Sample.provide`. В окне «элементы» разверните узел типа "Задача" и выберите один из элементов.  
  
5.  Сохраните файл.  
  
     (Еще не закрывайте экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].)  
  
 Вы создали модель, которая содержит ссылку на элемент в другой модели ModelBus.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Разрешить ссылку в текстовом шаблоне ModelBus  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], откройте образец файла шаблона. Вставьте в него следующим образом.  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     Обратите внимание на следующие моменты.  
  
    1.  `hostSpecific` И `inherits` атрибуты `template` необходимо задать директиву.  
  
    2.  Потребитель модели осуществляется в обычном режиме, через процессор директив, который был создан в этом DSL.  
  
    3.  Директивы сборки и импорта должен иметь доступ к ModelBus и типы поставщика DSL.  
  
    4.  Если вы знаете, что многие УПС связаны с той же модели, лучше вызывать CreateAdapter только один раз.  
  
2.  при сохранении шаблона; Убедитесь, что следующего вида в полученный текстовый файл.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Разрешить ссылку ModelBus в обработчика жестов  
  
1.  Закройте экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], если он выполняется.  
  
2.  Добавьте файл с именем MBConsumer\Dsl\Custom.cs и вставьте в него следующее.  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Нажмите клавиши CTRL+F5.  
  
4.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]откройте `Debugging\Sample.consume`.  
  
5.  Дважды щелкните одну фигуру.  
  
     Если устанавливается основная загрузочная запись для этого элемента, указанная модель открывается и указанный элемент.  
  
## <a name="see-also"></a>См. также  
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
