---
title: С помощью Visual Studio ModelBus в текстовом шаблоне | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3c6c3d9e35f14a03f8130982c562ba812ac11d6b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572303"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Использование Visual Studio ModelBus в текстовом шаблоне
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [с помощью Visual Studio ModelBus в текстовом шаблоне](https://docs.microsoft.com/visualstudio/modeling/using-visual-studio-modelbus-in-a-text-template).  
  
Если вы напишете текстовые шаблоны, считывающие модель, содержащую [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ссылки ModelBus, может потребоваться разрешения ссылок для доступа к целевой модели. В этом случае необходимо адаптировать текстовые шаблоны и на которую указывает ссылка предметно ориентированных языков (DSL):  
  
-   DSL, который является целевым объектом ссылки должен иметь адаптер ModelBus, настроенный для доступа на основе текстовых шаблонов. Если вы также получить доступ к DSL из другого кода, изменена конфигурация адаптера не требуется в дополнение к стандартный адаптер ModelBus.  
  
     Диспетчер адаптера должен наследовать от <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> и должен иметь атрибут `[HostSpecific(HostName)]`.  
  
-   Шаблон должен наследовать от <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Если вы хотите прочитать модели DSL, которые не содержат ссылок ModelBus, можно использовать процессоры директив, которые создаются в проекте DSL. Дополнительные сведения см. в разделе [доступ к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).  
  
 Дополнительные сведения о текстовых шаблонах см. в разделе [создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Создание адаптера шины модели для доступа на основе текстовых шаблонов  
 Чтобы разрешить ссылку ModelBus в текстовом шаблоне, целевого DSL должен иметь совместимый адаптера. Выполнение текстовых шаблонов в отдельном домене приложения из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] документа редакторы и, следовательно, адаптер для загрузки модели вместо обращения к ним через DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Чтобы создать адаптер ModelBus, которая совместима с помощью текстовых шаблонов  
  
1.  Если целевой объект в решение DSL не содержит **ModelBusAdapter** проект, создайте его с помощью мастера расширение Modelbus:  
  
    1.  Скачайте и установите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширение ModelBus, если вы еще не сделали это. Дополнительные сведения см. в разделе [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Откройте файл определения DSL. Щелкните правой кнопкой мыши область конструктора, а затем нажмите кнопку **включить Modelbus**.  
  
    3.  В диалоговом окне выберите **я хочу предоставить этот DSL для ModelBus**. Если вы хотите, чтобы предоставить свои модели и получать ссылки на другие DSL, можно выбрать оба варианта.  
  
    4.  Нажмите кнопку **ОК**. В решение DSL будет добавлен новый проект ModelBusAdapter.  
  
    5.  Нажмите кнопку **преобразовать все шаблоны**.  
  
    6.  Выполните повторную сборку решения.  
  
2.  Если вы хотите получить доступ к DSL из текстового шаблона и из другого кода, например команды, дублировать **ModelBusAdapter** проекта:  
  
    1.  В проводнике Windows скопируйте и вставьте в папку, содержащую **ModelBusAdapter.csproj**.  
  
    2.  Переименуйте файл проекта (например, чтобы **T4ModelBusAdapter.csproj**).  
  
    3.  В **обозревателе решений**, щелкните правой кнопкой мыши узел решения, укажите **добавить**, а затем нажмите кнопку **существующий проект**. Найдите новый проект адаптера, **T4ModelBusAdapter.csproj**.  
  
    4.  В каждом `*.tt` файл нового проекта, изменение пространства имен.  
  
    5.  Щелкните правой кнопкой мыши новый проект в обозревателе решений и выберите пункт Свойства. В редакторе свойств измените имена созданную сборку и пространство имен по умолчанию.  
  
    6.  В проекте DslPackage добавьте ссылку на проект адаптера, чтобы она содержала ссылки на обоих адаптеров.  
  
    7.  В DslPackage\source.extension.tt добавьте строку, которая ссылается на проект адаптера.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Преобразовать все шаблоны** и перестройте решение. Ошибки сборки не должно выполняться.  
  
3.  В новом проекте адаптера добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  В файл AdapterManager.tt:  
  
    -   Измените объявление AdapterManagerBase, чтобы он наследовался от <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Замените атрибут HostSpecific перед классом AdapterManager, в конце файла. Удалите следующую строку:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Вставьте следующую строку:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Этот атрибут фильтрует набор адаптеров, который доступен при modelbus потребитель выполняет поиск адаптер.  
  
5.  **Преобразовать все шаблоны** и перестройте решение. Ошибки сборки не должно выполняться.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Написание текстового шаблона, который может разрешать ссылки ModelBus  
 Как правило начните с шаблона, который считывает и создает файлы из DSL «источника». Этот шаблон используется директива, созданный в исходный проект доменного языка для чтения исходных файлов модели так, как описано в [доступ к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md). Тем не менее к исходному DSL содержит ссылки ModelBus на «target» DSL. Таким образом, необходимо включить код шаблона для разрешения ссылок и доступа к целевой DSL. Поэтому необходимо адаптировать шаблон, выполнив следующие действия:  
  
-   Измените базовый класс шаблона, <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Включить `hostspecific="true"` в директиве template.  
  
-   Добавьте ссылки на сборки для целевого DSL и его адаптер, а также для включения ModelBus.  
  
-   Директива, который создается как часть целевого DSL не обязательно.  
  
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
  
 При выполнении этого текстового шаблона `SourceDsl` директива загружает файл `Sample.source`. Шаблон можно обращаться к элементам модели, начиная с `this.ModelRoot`. Код можно использовать классы доменов и свойства этого DSL.  
  
 Кроме того шаблон может разрешить ссылки ModelBus. Там, где ссылки указывают на целевой модели, директивы сборки позволить коду использовать доменные классы и свойства этой модели DSL.  
  
-   Если вы не используете директива, которая создается в проекте DSL, должен содержать следующее.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Используйте `this.ModelBus` для получения доступа к ModelBus.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Пошаговое руководство: Тестирование текстового шаблона, использующего ModelBus  
 В этом пошаговом руководстве выполните следующие действия.  
  
1.  Создайте два DSL. Один DSL *потребителя*, имеет `ModelBusReference` свойство, которое может ссылаться на другие DSL, *поставщика*.  
  
2.  Создайте два адаптера ModelBus в поставщике: одна для доступа к из текстовых шаблонов, другой — для обычного кода.  
  
3.  Создайте экземпляр модели доменных языков в одном проекте экспериментальных.  
  
4.  Значение свойства домена в одной модели, чтобы указать другой модели.  
  
5.  Написать обработчик, дважды щелкните файл, который открывает модели, которое указывает.  
  
6.  Напишете текстовый шаблон, можно загрузить первой модели, выполните ссылку на другой моделью и чтение другие модели.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Конструкция DSL, который доступен ModelBus  
  
1.  Создание нового решения DSL. Например Выбор шаблона решения потока задачи. Задайте имя языка `MBProvider` и расширение имени файла для «.provide».  
  
2.  В схеме определения DSL, щелкните правой кнопкой мыши пустую часть схемы, не расположено в верхней части и нажмите кнопку **включить Modelbus**.  
  
    -   Если вы не видите **включить Modelbus**, необходимо загрузить и установить расширение VMSDK ModelBus. Найти его на сайте VMSDK: [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  В **включить Modelbus** выберите **предложить этот DSL для ModelBus**, а затем нажмите кнопку **ОК**.  
  
     Новый проект, `ModelBusAdapter`, добавляется в решение.  
  
 Теперь у вас есть DSL, который может осуществляться из текстовых шаблонов с помощью ModelBus. Ссылки на него можно разрешить в коде команд, обработчиков событий или правила, работающих в домене приложения редактора файла модели. Тем не менее текстовых шаблонов выполняются в отдельном домене приложения и нет доступа к модели, когда она редактируется. Если вы хотите получить доступ к ссылок ModelBus на этот DSL из текстового шаблона, необходимо иметь отдельный ModelBusAdapter.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Для создания адаптера ModelBus, настроенный для текстовых шаблонов  
  
1.  В обозревателе Windows скопируйте и вставьте в папку, содержащую ModelBusAdapter.csproj.  
  
     Назовите папку T4ModelBusAdapter.  
  
     Переименуйте файл проекта T4ModelBusAdapter.csproj.  
  
2.  В обозревателе решений добавьте T4ModelBusAdapter MBProvider решение. Щелкните правой кнопкой мыши узел решения, выберите пункт **добавить**, а затем нажмите кнопку **существующий проект**.  
  
3.  Щелкните правой кнопкой мыши узел проекта T4ModelBusAdapter и выберите пункт Свойства. В окне свойств проекта измените **имя сборки** и **пространство имен по умолчанию** для `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  В каждом файле *.tt в T4ModelBusAdapter вставьте «T4» последней частью пространства имен, таким образом, чтобы строка выглядит следующим образом.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  В `DslPackage` , добавьте в проект ссылку на `T4ModelBusAdapter`.  
  
6.  В DslPackage\source.extension.tt, добавьте следующую строку в разделе `<Content>`.  
  
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
  
    2.  В конце файла вставьте перед классом AdapterManager следующий дополнительный атрибут.  
  
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
  
9. Нажмите кнопку **преобразовать все шаблоны** в заголовок обозревателя решений.  
  
10. Выполните повторную сборку решения. Нажмите кнопку F5.  
  
11. Проверьте работоспособность DSL, нажав клавишу F5. В экспериментальном проекте откройте `Sample.provider`. Закройте экспериментальный образец [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Теперь ModelBus ссылки на этот DSL можно разрешить в текстовых шаблонах, а также в обычный код.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Создать DSL со свойством домена ссылка ModelBus  
  
1.  Создайте новый доменный язык, с помощью шаблона решения минимальный язык. Имя языка MBConsumer и задать расширение имени файла для «.consume».  
  
2.  В проекте DSL добавьте ссылку на сборку MBProvider DSL. Щелкните правой кнопкой мыши `MBConsumer\Dsl\References` и нажмите кнопку **добавить ссылку**. В **Обзор** вкладке, найдите `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Это позволяет создавать код, который использует другие DSL. Если вы хотите создавать ссылки на несколько доменных языков, также добавьте их.  
  
3.  В схеме определения DSL, щелкните правой кнопкой мыши по диаграмме и нажмите кнопку **включить ModelBus**. В диалоговом окне выберите **включить этот DSL использовать ModelBus**.  
  
4.  В классе `ExampleElement`, добавить новое свойство домена `MBR`и в окне свойств задайте для нее тип `ModelBusReference`.  
  
5.  Щелкните правой кнопкой мыши свойство домена на схеме, а затем нажмите кнопку **изменить некоторые свойства ModelBusReference**. В диалоговом окне выберите **элемента модели**.  
  
     Задайте следующее диалоговое окно фильтра файлов.  
  
     `Provider File|*.provide`  
  
     Подстрока после "&#124;" фильтров, диалоговое окно выбора файла. Можно задать его, чтобы разрешить все файлы с помощью *.\*  
  
     В **тип элемента модели** , введите имена от одного или нескольких доменных классов в поставщике DSL (например, Company.MBProvider.Task). Они могут быть абстрактные классы. Если список не заполнено, пользователь может задать ссылку на любой элемент.  
  
6.  Закрыть диалоговое окно и **преобразовать все шаблоны**.  
  
 Вы создали DSL, который может содержать ссылки на элементы в другой DSL.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Создать ссылку ModelBus в другой файл в решении  
  
1.  В решении MBConsumer нажмите клавиши CTRL + F5. Экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] открывается в **MBConsumer\Debugging** проекта.  
  
2.  Добавьте копию Sample.provide для **MBConsumer\Debugging** проекта. Это необходимо, так как ссылка ModelBus необходимо обратиться к файлу, в том же решении.  
  
    1.  Щелкните правой кнопкой мыши проект "Отладка", выберите пункт **добавить**, а затем нажмите кнопку **существующий элемент**.  
  
    2.  В **Добавление элемента** диалоговое окно, настройте фильтр так, **все файлы (\*.\*)** .  
  
    3.  Перейдите к `MBProvider\Debugging\Sample.provide` и нажмите кнопку **добавить**.  
  
3.  Откройте `Sample.consume`.  
  
4.  Щелкните одной пример формы и в окне «Свойства» щелкните **[...]**  в свойстве MBR. В диалоговом окне щелкните **Обзор** и выберите `Sample.provide`. В окне «элементы» разверните узел типа "Задача" и выберите один из элементов.  
  
5.  Сохраните файл.  
  
     (Еще не закрывайте экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].)  
  
 Вы создали модель, которая содержит ссылку ModelBus на элемент в другой модели.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Разрешить ссылку ModelBus в текстовом шаблоне  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], откройте пример текстового файла шаблона. Вставьте в него следующим образом.  
  
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
  
    1.  `hostSpecific` И `inherits` атрибуты `template` директива должно иметь значение.  
  
    2.  Потребитель модели осуществляется обычным образом через процессор директив, который был создан в этом DSL.  
  
    3.  Директивы сборки и импорта должен иметь возможность доступа к ModelBus и типы поставщика DSL.  
  
    4.  Если вы знаете, что многие MBR связаны с той же модели, лучше вызывать CreateAdapter только один раз.  
  
2.  при сохранении шаблона; Убедитесь, что следующего вида в полученный текстовый файл.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Разрешить ссылку ModelBus в обработчика жестов  
  
1.  Закройте экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], если она запущена.  
  
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
  
4.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]откройте `Debugging\Sample.consume`.  
  
5.  Дважды щелкните одну фигуру.  
  
     Если для этого элемента установлен MBR, указанная модель открывается и ссылочного элемента.  
  
## <a name="see-also"></a>См. также  
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)



