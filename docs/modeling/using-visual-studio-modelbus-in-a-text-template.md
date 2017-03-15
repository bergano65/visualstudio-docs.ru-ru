---
title: "Использование Visual Studio ModelBus в текстовом шаблоне | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# Использование Visual Studio ModelBus в текстовом шаблоне
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При написании текстовых шаблонов, которые считывают модель, содержащую [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ссылка ModelBus, может понадобиться разрешить ссылки для доступа к целевые модели.  В этом случае необходимо использовать текстовые шаблоны и ссылочные доменных языков \(DSLs\):  
  
-   DSL, который является целевым объектом ссылки, должен иметь адаптер ModelBus, настроенный для доступа из текстовых шаблонов.  Если также доступ к DSL из другого кода, вновь скомпонованный адаптер является обязательным в дополнение к стандартному адаптеру ModelBus.  
  
     Диспетчер адаптера должен наследовать из <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> и иметь атрибут  `[HostSpecific(HostName)]`.  
  
-   Шаблон должен наследовать из <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Если нужно считывать модели DSL, которые не содержат ссылок ModelBus, можно использовать процессоры директив, создаваемых в проектах DSL.  Дополнительные сведения см. в разделе [Обращение к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).  
  
 Дополнительные сведения о текстовых шаблонах см. в разделе [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## Создать адаптер шины модели для доступа из текстовых шаблонов  
 Включение ссылка ModelBus в текстовом шаблоне, целевой объект DSL должен иметь совместимые адаптер.  Текстовые шаблоны выполнялись в отдельном домене приложения из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редакторы документа, и поэтому должны загрузить модель адаптера вместо обращения к ним через DTE.  
  
#### Создание адаптера ModelBus, который совместим с текстовыми шаблонами  
  
1.  Если решение DSL целевого объекта не имеет a **ModelBusAdapter** проект создает его с помощью мастера расширения Modelbus.  
  
    1.  Загрузите и установите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Расширение ModelBus, если вы еще не сделали это.  Дополнительные сведения см. в разделе [Пакет SDK для визуализации данных и моделирования](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Откройте файл определения DSL.  Щелкните правой кнопкой мыши область конструктора и выберите пункт **Включите Modelbus**.  
  
    3.  В диалоговом окне выберите **Сведения об предоставить этот DSL к ModelBus**.  Можно выбрать оба параметра, если необходимо предоставить этот DSL и ее модели и использовать ссылки на другой DSLs.  
  
    4.  Нажмите кнопку **ОК**.  Новый проект "ModelBusAdapter" добавляется в решение DSL.  
  
    5.  Нажать **Преобразовать все шаблоны**.  
  
    6.  Вновь Выполните сборку решения.  
  
2.  Если необходимо получить доступ к DSL и из текстового шаблона и от другого кода, как команда, дубликат **ModelBusAdapter** проект:  
  
    1.  В проводнике скопируйте и вставьте папку, содержащую **ModelBusAdapter.csproj**.  
  
    2.  Переименуйте файл проекта \(например, **T4ModelBusAdapter.csproj**\).  
  
    3.  IN **Обозреватель решений**щелкните правой кнопкой мыши узел решения, укажите  **Добавить**, а затем нажмите кнопку  **Существующий проект**.  Найдите новый проект адаптера **T4ModelBusAdapter.csproj**.  
  
    4.  в каждом `*.tt` файл нового проекта, изменяет пространство имен.  
  
    5.  Щелкните правой кнопкой мыши новый проект в обозревателе решений и выберите пункт свойства.  В редакторе свойств измените имя создаваемой сборки и пространства имен по умолчанию.  
  
    6.  В проекте DslPackage добавьте ссылку на новый проект адаптера, чтобы он будет иметь ссылки на оба адаптеров.  
  
    7.  В DslPackage \\ source.extension.tt, добавить линию, которая ссылается на новый проект адаптера.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Преобразовать все шаблоны** и перестройте решение.  Ошибки построения не должны выполняться.  
  
3.  Адаптера в новом проекте добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  в AdapterManager.tt:  
  
    -   Измените объявление AdapterManagerBase таким образом, чтобы он будет наследовать из <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   В конце файла замените атрибуту HostSpecific перед классом AdapterManager.  Удалите следующую линия.  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Вставьте следующую распространитель:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Этот атрибут фильтрует набор адаптеров, который доступен только тогда, когда объект\-получатель modelbus выполняет поиск адаптеров.  
  
5.  **Преобразовать все шаблоны** и перестройте решение.  Ошибки построения не должны выполняться.  
  
## Написание текстового шаблона, который может разрешить ссылки ModelBus  
 Как правило, разработанных с шаблоном, который считывает и создает файлы из "источник" DSL.  Этот шаблон используется директива, которая создается в проекте DSL источника чтения файлов исходной модели способом, который описан в пределах [Обращение к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).  Однако источник DSL содержит ссылки ModelBus на "целевой объект" DSL.  Поэтому необходимо включить код шаблона для разрешения ссылок и доступа к целевой объект DSL.  Поэтому следует обеспечить шаблон, выполнив следующие шаги.  
  
-   Измените базовый класс шаблона <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Include `hostspecific="true"` в директиве шаблона.  
  
-   Добавьте ссылки на сборки к целевому объекту DSL и его адаптеру и включить ModelBus.  
  
-   Не требуется директива, которая создается в рамках целевого объекта DSL.  
  
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
    // (Let’s assume they’re all in the same model file):  
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
  
 При выполнении данного текстового шаблона `SourceDsl` директива загружает файл  `Sample.source`.  Шаблон может получить доступ к этой модели, начиная с элементов `this.ModelRoot`.  Код может использовать доменных классы и свойства этого DSL.  
  
 Кроме того, шаблон может разрешить ссылки ModelBus.  Если контрольная точка в целевой модели, директивы сборки препятствовала использовании кода доменных классы и свойства DSL этой модели.  
  
-   Если не используется директива, которая создается проектом DSL, необходимо также включить следующее.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Используйте `this.ModelBus` получить доступ к ModelBus.  
  
## Пошаговое руководство. Проверка текстового шаблона, который использует ModelBus  
 В этом пошаговом руководстве вы выполните следующие действия:  
  
1.  Конструкция 2 DSLs.  Один DSL, объект\-получательимеет a `ModelBusReference` свойство, которое может ссылаться на другой, DSL Поставщик.  
  
2.  Создание 2 адаптера ModelBus в поставщике. одно для доступа с текстовыми шаблонами, другой \- для обычного кода.  
  
3.  Создание моделей экземпляра DSLs в одном экспериментальном проекте.  
  
4.  Установите свойство домена в одной модели до точки к другой модели.  
  
5.  Напишите обработчик двойного щелчка, который открывает, указывающая на модель.  
  
6.  Создайте текстовый шаблон, который может загрузить первую модель, выполните ссылку на другой модели, а чтение другой модели.  
  
#### Постройте DSL, который доступен ModelBus  
  
1.  Создайте новое решение DSL.  Для этого примера выберите шаблон решения потока задач.  Задайте имя языка к MBProvider и расширение имени файла на ".provide".  
  
2.  В схеме определения DSL, щелкните правой кнопкой мыши пустую часть схемы, которая не находится в верхней части, а затем выберите команду **Включите Modelbus**.  
  
    -   Если он отсутствует **Включите Modelbus**необходимо загрузить и установить расширение VMSDK ModelBus.  Найдите на сайте VMSDK: [Пакет SDK для визуализации данных и моделирования](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  в **Включите Modelbus** диалоговое окно открывается  **Предоставьте этот DSL к ModelBus**, а затем нажмите кнопку  **ОК**.  
  
     Новый проект `ModelBusAdapter`добавьте в решение.  
  
 Теперь имеется DSL, который может быть получен текстовыми шаблонами с помощью ModelBus.  Ссылки на него можно включить в коде команд, обработчиков событий или правил, которые работают в домене приложения файла модели редактора.  Однако запуск текстовых шаблонов в отдельном домене приложения и не может получить доступ к модели при ее изменение.  Если необходимо получить доступ к этому ссылка ModelBus DSL из текстового шаблона, необходимо иметь отдельные ModelBusAdapter.  
  
#### Создание адаптера ModelBus, настроенный для текстовых шаблонов  
  
1.  В проводнике скопируйте и вставьте папку, содержащую ModelBusAdapter.csproj.  
  
     Назовите папку T4ModelBusAdapter.  
  
     Переименуйте файл проекта T4ModelBusAdapter.csproj.  
  
2.  В обозревателе решений добавьте в решение T4ModelBusAdapter MBProvider.  Щелкните правой кнопкой мыши узел решения, укажите **Добавить**, а затем нажмите кнопку  **Существующий проект**.  
  
3.  Щелкните правой кнопкой мыши узел проекта T4ModelBusAdapter и выберите пункт свойства.  в окне свойств проекта, измените **Имя сборки** и  **Пространство имен по умолчанию** В  `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  В каждом файле \*.tt в T4ModelBusAdapter, вставка "T4" в последней части пространства имен, так что линия выглядит следующим образом.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  в `DslPackage` проект добавляет в проект ссылку на  `T4ModelBusAdapter`.  
  
6.  В DslPackage \\ source.extension.tt добавьте следующую линия вниз `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  в `T4ModelBusAdapter` добавьте ссылку на проект:  **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Откройте T4ModelBusAdapter \\ AdapterManager.tt:  
  
    1.  Измените базовый класс для AdapterManagerBase <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  Эта часть файла теперь похожа на следующее.  
  
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
  
    2.  В конце файла вставьте следующий дополнительный атрибут перед классом AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Результат выглядит следующим образом.  
  
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
  
9. Нажать **Преобразовать все шаблоны** в заголовке окна обозреватель решений.  
  
10. Вновь Выполните сборку решения.  Нажмите F5.  
  
11. Убедитесь, что DSL работает, нажав клавишу F5.  В экспериментальном проекте, открытие `Sample.provider`.  Закройте экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Ссылка ModelBus на этот DSL теперь можно разрешить в текстовых шаблонах, а также в обычном коде.  
  
#### Постройте DSL с свойством домена ссылка ModelBus  
  
1.  Создайте новый DSL с помощью минимального шаблона решения языка.  Назовите язык MBConsumer и присвойте расширение имени файла на ".consume".  
  
2.  В проекте DSL добавьте ссылку на сборку MBProvider DSL.  Щелкните правой кнопкой мыши  `MBConsumer\Dsl\References` затем перейдите  **Добавление ссылки**.  в **Обзор** вкладка находит  `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Это позволяет создать код, который использует другой DSL.  Если нужно создать ссылки на несколько DSLs, добавьте их.  
  
3.  В схеме определения DSL, щелкните правой кнопкой мыши схему и выберите команду **Включите Modelbus**.  В диалоговом окне выберите **Разрешить этот DSL, чтобы использовать ModelBus**.  
  
4.  в классе `ExampleElement`добавьте новое свойство домена  `MBR`и в окне свойств, типом  `ModelBusReference`.  
  
5.  Щелкните правой кнопкой мыши свойство домена, а затем щелкните на схеме **Свойства ModelBusReference правки определенные**.  В диалоговом окне выберите **Элемент модели**.  
  
     Задание фильтра диалогового окна файла.  
  
     `Provider File|*.provide`  
  
     Подстрока после "&#124;" фильтр для диалогового окна выбора файла.  Можно задать его, чтобы разрешить любые файлы с помощью \*.\*  
  
     в **Тип элемента модели** введите имена одного штуфа несколько доменных классов поставщика DSL \(например, Company.MBProvider.Task\).  Они могут быть абстрактными классами.  Если оставить пустым списка, пользователь может задать ссылку к любому элементу.  
  
6.  Закройте диалоговое окно и **Преобразовать все шаблоны**.  
  
 Вы создали DSL, который может содержать ссылки на элементы в другом DSL.  
  
#### Создайте ссылка ModelBus на другой файл решения  
  
1.  В решении MBConsumer, нажмите клавиши CTRL\+F5.  Экспериментальном экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] открытые в  **MBConsumer\\Debugging** этот проект.  
  
2.  Добавление копии Sample.provide к **MBConsumer\\Debugging** этот проект.  Это необходимо, так как ссылка ModelBus должна ссылаться на файл в том же решении.  
  
    1.  Щелкните правой кнопкой мыши проект, выберите пункт отладки **Добавить**, а затем нажмите кнопку  **Существующий элемент**.  
  
    2.  в **Добавить элемент** откроется диалоговое окно выберите фильтр к  **Все файлы \(\*.\*\)**.  
  
    3.  Перейдите на `MBProvider\Debugging\Sample.provide` затем перейдите  **Добавить**.  
  
3.  Откройте программу `Sample.consume`.  
  
4.  См. пример shape и в окне свойств щелкните \[...\] в свойстве MBR.  В диалоговом окне нажмите кнопку **Обзор** и select  `Sample.provide`.  В окне элементов разверните задача типа и выберите один из элементов.  
  
5.  Сохраните файл.  
  
     \(Пока не закрыть экспериментальном экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].\)  
  
 Модель создана, которая содержит ссылку ModelBus на элемент в другой модели.  
  
#### Разрешить ссылка ModelBus в текстовом шаблоне  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]открыть файл текстового шаблона.  Установите его содержимое следующим образом.  
  
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
  
    1.  `hostSpecific` и  `inherits` атрибуты   `template` рекомендация должна быть задана.  
  
    2.  Модель получить доступ к обычным способом объекта\-получателя через процессор директив, созданный в этом DSL.  
  
    3.  Директивы сборки и импорта должны иметь возможность доступа к ModelBus и типы поставщика DSL.  
  
    4.  Если известно, что многие MBR связаны с одной и той же модели, лучше вызывать CreateAdapter только один раз.  
  
2.  Сохраните шаблон.  Убедитесь, что конечный текстовый файл выглядит следующим образом.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### Разрешить ссылка ModelBus в обработчик жестов  
  
1.  Закройте экспериментальном экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], если он выполняется.  
  
2.  Добавьте файл с именем MBConsumer \\ Dsl \\ Custom.cs и задайте его содержимое следующим образом.  
  
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
  
3.  Нажмите клавиши CTRL\+F5.  
  
4.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]открытый  `Debugging\Sample.consume`.  
  
5.  Дважды щелкните одну форму.  
  
     Если имеется набор MBR в этом элементе, упоминаемая модель открывается и упоминаемый элемент выбран.  
  
## См. также  
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)