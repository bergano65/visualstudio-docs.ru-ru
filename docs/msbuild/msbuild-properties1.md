---
title: "MSBuild Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Свойства MSBuild"
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Properties1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Свойства являются парами имя значение, которые могут использоваться для настройки построений. Свойства используются для передачи значений задачам, оценки условий и сохранения значений, которые будут указывать ссылки в файле проекта.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Определение и ссылки на свойства в файле проекта  
 Для объявления свойств создается элемент с именем свойства как дочерний [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) элемента. Например, следующий код XML создает свойство с именем `BuildDir` имеет значение `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 В файле проекта ссылка на свойства используется синтаксис $(`PropertyName`). Например свойство в предыдущем примере указывается с помощью $(BuildDir).  
  
 Значения свойств можно изменить путем переопределения свойства.  `BuildDir` Свойству можно присвоить новое значение, используя этот XML-КОД:  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Свойства оцениваются в порядке, в котором они отображаются в файле проекта. Новое значение для `BuildDir` необходимо объявить после присвоения прежнего значения.  
  
## <a name="reserved-properties"></a>Зарезервированные свойства  
 MSBuild резервирует некоторые имена свойств для хранения информации о файле проекта и двоичных файлах MSBuild. Эти свойства ссылаются с помощью нотации $, так же, как любого другого свойства. Например $(MSBuildProjectFile) возвращает полное имя файла проекта, включая расширение имени файла.  
  
 Дополнительные сведения см. в разделе [как: ссылки на имя или расположение файла проекта](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) и [MSBuild зарезервированные и стандартные свойства](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Свойства среды  
 Так же, как ссылки на зарезервированные свойства можно ссылаться на переменные среды в файлах проектов. Например, чтобы использовать `PATH` переменной среды в файле проекта, укажите $(Path). Если проект содержит определение свойства, которое совпадает с именем свойства среды, свойство из файла проекта переопределяет значение переменной среды.  
  
 Каждый проект MSBuild содержит блок изолированной среды: только видит чтения и записывает их блока.  MSBuild только считывает Инициализирует коллекцию свойств, прежде чем вычисляется файл проекта или встроенные переменные среды. После этого свойства среды являются статическими, то есть каждый порожденных в отобразившемся с одинаковыми именами и значениями.  
  
 Чтобы получить текущее значение переменные среды из порожденных средство, используйте [функции свойства](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. Однако рекомендуется использовать параметр задачи <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Свойства среды, заданные в этот массив строк может быть передан средство порожденных без влияния на переменные среды.  
  
> [!TIP]
>  Не все переменные среды считываются в качестве исходного свойства. Любая переменная среды, имя которого не допустимый MSBuild имена свойств, таких как «386» учитывается.  
  
 Дополнительные сведения см. в разделе [Практическое руководство: использование переменных среды в построении](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md).  
  
## <a name="registry-properties"></a>Свойства реестра  
 Вы можете чтения значений системного реестра, используя следующий синтаксис, где `Hive` — это куст реестра (например, HKEY_LOCAL_MACHINE), `Key` — имя раздела, `SubKey` — имя подраздела, и `Value` значение подраздела.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Чтобы получить значение подраздела по умолчанию, опустите `Value`.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Это значение реестра можно использовать для инициализации свойства построения. Например чтобы создать свойство построения, которое представляет Домашняя страница Visual Studio веб-браузера, используйте следующий код:  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Глобальные свойства  
 MSBuild можно задавать свойства в командной строке с помощью **/property** (или **/p**) переключения. Эти глобальные значения свойств переопределяют значения свойств, заданные в файле проекта. Это относится к свойствам среды, но не включает зарезервированные свойства, которые нельзя изменить.  
  
 В следующем примере задается глобальный `Configuration` Свойства `DEBUG`.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Глобальные свойства можно также задать или изменять для дочерних проектов многопроектных построений, используя `Properties` атрибут задачи MSBuild. Дополнительные сведения см. в разделе [задачи MSBuild](../msbuild/msbuild-task.md).  
  
 Если задать свойство с помощью `TreatAsLocalProperty` атрибут в теге проекта, что значение глобального свойства не переопределяется значение свойства, которое задается в файле проекта. Дополнительные сведения см. в разделе [элемент Project (MSBuild)](../msbuild/project-element-msbuild.md) и [как: построение одинаковых исходных файлов с различными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Функции свойств  
 Начиная с .NET Framework версии 4, функции свойств можно использовать для оценки скрипты MSBuild. Можно читать системное время, сравнивать строки, регулярные выражения и выполнять многие другие действия в скрипте построения без использования задач MSBuild.  
  
 Для работы с любым значением свойства можно использовать методы строки (экземпляра) и может вызывать статические методы многих системных классов. Например можно задать свойства построения текущую дату как следующим.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Дополнительные сведения и список функций свойств см. в разделе [функции свойства](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Создание свойств во время выполнения  
 Свойства находится за пределами `Target` элементы, значения присваиваются на этапе оценки построения. На этапе выполнения свойства может быть создано или изменено следующим образом:  
  
-   Можно создать свойство посредством любой задачи. Для создания свойства, [задачи](../msbuild/task-element-msbuild.md) элемент должен иметь дочерний [вывода](../msbuild/output-element-msbuild.md) элемент, имеющий `PropertyName` атрибута.  
  
-   Можно создать свойство посредством [CreateProperty](../msbuild/createproperty-task.md) задачи. Этот метод рекомендуется использовать.  
  
-   Начиная с .NET Framework 3.5, `Target` элементы могут содержать `PropertyGroup` элементы, которые могут содержать объявления свойств.  
  
## <a name="storing-xml-in-properties"></a>Сохранение XML в свойствах  
 Свойства могут содержать произвольные XML, предназначенные для передачи значений задачам или отображения информации журналов. В следующем примере показан `ConfigTemplate` Свойства, которое имеет значение, содержащее XML и другие свойства ссылки. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] заменяет ссылки на свойства соответствующими значениями свойств. Значения свойств присваиваются в порядке, в котором они появляются. Таким образом, в этом примере `$(MySupportedVersion)`, `$(MyRequiredVersion)`, и `$(MySafeMode)` должен уже определен.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>См. также  
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)  
 [Практическое руководство: использование переменных среды в построении](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)   
 [Практическое руководство: ссылки на имя или расположение файла проекта](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md)   
 [Практическое руководство: построение одинаковых исходных файлов с различными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild зарезервированные и стандартные свойства](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Элемент Property (MSBuild)](../msbuild/property-element-msbuild.md)