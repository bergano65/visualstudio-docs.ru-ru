---
title: "Сохранение данных в файле проекта MSBuild | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b2bb73602a6cba07fe9cbde4ddae4219f5a2b350
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Сохранение данных в файле проекта MSBuild
Подтип проекта может потребоваться сохранить подтипа данных в файле проекта для последующего использования. Подтип проекта использует долговременного хранения файла проекта для отвечать следующим требованиям:  
  
1.  Сохранение данных, используемых в процессе построения проекта. (Дополнительные сведения о Microsoft Build Engine см. в разделе [MSBuild](../../msbuild/msbuild.md).) Сведения, связанные с построением можно:  
  
    1.  Данные, зависящие от конфигурации. То есть данные, хранящиеся в элементы MSBuild с условиями пусты или отсутствуют.  
  
    2.  Данные, зависящие от конфигурации. То есть данные, хранящиеся в элементы MSBuild, определяется для конфигурации конкретного проекта. Пример:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Сохранение данных, не имеет значения для построения. Эти данные могут выражаться в свободной форме XML, который не проверяется на соответствие схеме XML.  
  
    1.  Данные, зависящие от конфигурации.  
  
    2.  Данные, зависящие от конфигурации.  
  
## <a name="persisting-build-related-information"></a>Сохранение информации, связанные с построением  
 Сохранение данных полезно для построения проекта обрабатываться с помощью MSBuild. Система MSBuild сохраняет главную таблицу данных, связанные с построением. Подтипы проекта отвечают за доступ к данным для получения и задания значений свойств. Подтипы проекта также можно расширить таблицы данных, связанные с построением путем добавления дополнительных свойств, которые необходимо сохранить и удалять свойства, поэтому они не сохраняются.  
  
 Для изменения данных MSBuild подтипом проекта отвечает за извлечение из базовой системы проектов через объект свойства MSBuild <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>Представляет интерфейс, реализованный в основная система проектов и статистической обработки запросов подтип проекта для него, выполнив `QueryInterface`.  
  
 В следующей процедуре представлены действия по удалению свойства с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Чтобы удалить свойство из файла проекта MSBuild  
  
1.  Вызовите `QueryInterface` на <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> подтипа проекта.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> с `pszPropName` значение свойства, которые требуется удалить.  
  
### <a name="persisting-non-build-related-information"></a>Сведения, связанные с сохранения без построения  
 Сохранение данных в файлах проекта, не имеет значения для построения обрабатывается с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Можно реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> в главной `project subtype aggregator` объекта, `project subtype project configuration` объект или оба.  
  
 Следующие моменты рассматриваются основные понятия, касающиеся сохраняемости связанных данных, отличных от сборки.  
  
-   Базовый проект вызывает в объекте основной проект подтип (внешней проекта подтип) инвентаризации программного обеспечения для загрузки и сохранения независимые данные конфигурации, а его в проект конфигурации проекта подтип объекты на загрузку или сохранение зависят от конфигурации данные.  
  
-   Базовый проект вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> несколько раз для каждого уровня статистической обработки подтип проекта и передает идентификатор GUID для каждого уровня.  
  
-   Базовый проект передает или получает XML-фрагмент, который предназначен для конкретного проекта подтипом и использует этот механизм как способ сохранения состояния между уровни статистической обработки.  
  
-   Подтип внешней проекта вызывает базовый проект <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>реализацию, передавая идентификатор GUID. Если идентификатор GUID относится к внешней проекта подтип, он обрабатывает вызов самостоятельно. в противном случае в противном случае вызов подтип внутреннего проекта и т. д., пока не будет найден подтипом проекта, соответствующий идентификатор GUID.  
  
-   Подтип проекта можно также изменить XML-фрагмент до или после он делегирует вызов подтип внутреннего проекта. В следующем примере показано фрагмент из файла проекта, где имя файла, содержащего свойства, относящиеся к подтипу проекта передается подтип этого проекта.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)