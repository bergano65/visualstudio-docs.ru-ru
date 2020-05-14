---
title: Сохраняющиеся данные в файле проекта MSBuild (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706698"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Сохранение данных в файле проекта MSBuild
Подтипу проекта может потребоваться сохранить данные, связанные с подтипом, в файле проекта для последующего использования. Подтип проекта использует сохранение файла проекта для удовлетворения следующих требований:

1. Устойчивые данные, используемые в рамках создания проекта. (Для получения дополнительной информации о Microsoft Build Engine, [см. MSBuild](../../msbuild/msbuild.md).) Информация, связанная с сборкой, может:

    1. Независят от конфигурации данные. То есть данные, хранящиеся в элементах MSBuild с пустыми или отсутствующими условиями.

    2. Зависящие от конфигурации данные. То есть данные, хранящиеся в элементах MSBuild, которые обусловлены для конкретной конфигурации проекта. Пример:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Упорные данные, которые не имеют отношения к сборке. Эти данные могут быть выражены в свободной форме XML, которая не проверяется против схемы XML.

    1. Независят от конфигурации данные.

    2. Зависящие от конфигурации данные.

## <a name="persisting-build-related-information"></a>Сохраняющаяся информация, связанная с сборкой
 Сохранение данных, полезных для создания проекта, обрабатывается с помощью MSBuild. Система MSBuild поддерживает основную таблицу информации, связанной со сборкой. Подтипы проекта отвечают за доступ к этим данным для получения и установки значений свойств. Подтипы проекта могут также увеличить таблицу данных, связанных со сборкой, путем добавления дополнительных свойств, которые будут сохраняться, и удаления свойств, чтобы они не сохранялись.

 Чтобы изменить данные MSBuild, подтип проекта отвечает за извлечение объекта свойства <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>MSBuild из базовой проектной системы через. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>— это интерфейс, реализованный в основной системе проекта и агрегирующих `QueryInterface`подтипные запросы проекта для него при запуске.

 Следующая процедура определяет шаги для удаления <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>свойства с помощью.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Удаление свойства из файла проекта MSBuild

1. Займите `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> подтип проекта.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> Звоните `pszPropName` с набором в свойство, которые вы хотите удалить.

### <a name="persisting-non-build-related-information"></a>Сохраняющаяся непостройная связанная с этим информация
 Сохранение данных в файлах проекта, которые не <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>имеет значения для сборки, обрабатывается через.

 Вы можете <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> реализовать `project subtype aggregator` на главном `project subtype project configuration` объекте, объекте или обоих.

 В следующих пунктах излагаются основные концепции, касающиеся сохранения непостройки соответствующей информации.

- Базовый проект требует, чтобы основной подтип проекта (т.е. внешний подтип проекта) агрегатор загружал и сохранял независимые данные конфигурации, а также призывал объекты конфигурации подтипа проекта загрузить или сохранить зависимые данные конфигурации конфигурации.

- Базовый проект вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> несколько раз для каждого уровня агрегации подтипов проекта и передает GUID для каждого уровня.

- Базовый проект проходит или получает фрагмент XML, посвященный конкретному подтипу проекта, и использует этот механизм как способ сохранения состояния между уровнями агрегирования.

- Базовый проект называет <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>реализацию подтипа внешнего проекта, проходящую в GUID. Если GUID относится к подтипу внешнего проекта, он обрабатывает сам вызов; в противном случае он делегирует вызов внутреннему подтипу проекта и так далее, пока не будет найден подтип проекта, которым соответствует GUID.

- Подтип проекта может также изменять фрагмент XML до или после его делегировать вызов внутреннему подтипу проекта. В следующем примере показан отрывок из файла проекта, где имя файла, содержащего свойства, характерные для подтипа проекта, передается подтипу проекта.

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
- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)
