---
title: Регистрация шаблонов проектов и элементов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd61d4bf97ce25d291268856a3e85729c98c1312
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658403"
---
# <a name="registering-project-and-item-templates"></a>Регистрация шаблонов проектов и элементов
Типы проектов необходимо регистрировать каталоги, где находятся их шаблонов проектов и элементов проекта. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует сведения о регистрации, связанные с типами вашего проекта, чтобы определить, что нужно показывать в **Добавление нового проекта** и **Добавление нового элемента** диалоговым окнам.

 Дополнительные сведения о шаблонах см. в разделе [добавление проектов и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Записи реестра для проектов
 Ниже приведены примеры записей реестра в разделе HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*версии*>. В сопутствующей таблицах описываются элементы, используемые в примерах.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|name|Тип|Описание|
|----------|----------|-----------------|
|@|REG_SZ|Имя по умолчанию для проектов такого рода.|
|DisplayName|REG_SZ|Идентификатор ресурса имени должно быть извлечено из вспомогательной библиотеки DLL зарегистрирован в пакеты.|
|Пакет|REG_SZ|Идентификатор класса пакета зарегистрирован в пакеты.|
|ProjectTemplatesDir|REG_SZ|По умолчанию путь к файлам проекта шаблона. Файлы шаблонов проекта отображаются по **новый проект** шаблона.|

### <a name="registering-item-templates"></a>Регистрация шаблонов элементов
 Необходимо зарегистрировать каталог, где хранятся шаблоны элементов.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| name | Тип | Описание |
|--------------------------|-----------| - |
| @ | REG_SZ | Идентификатор ресурса для шаблонов добавить элемент. |
| TemplatesDir | REG_SZ | Путь проекта элементов, отображаемых в диалоговом окне для **Добавление нового элемента** мастера. |
| TemplatesLocalizedSubDir | REG_SZ | Идентификатор ресурса для строки с именем TemplatesDir в подкаталог, который содержит локализованных шаблонов. Так как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] каждой вспомогательной библиотеки DLL могут содержать разные локализованные подкаталог с именем, загружает строковый ресурс из вспомогательные библиотеки DLL, если их нет. |
| SortPriority | REG_DWORD | Задайте SortPriority, определяющую порядок отображения шаблонов в **Добавление нового элемента** диалоговое окно. Большие значения SortPriority объявленных ранее в списке шаблонов. |

### <a name="registering-file-filters"></a>Регистрация фильтры файлов
 При желании вы можете зарегистрировать фильтры, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует при запросе у имен файлов. Например [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] фильтрации для **открыть файл** используется диалоговое окно:

 **Visual C# Files (\*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl);\*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Для поддержки регистрации несколько фильтров, каждый фильтр регистрируется в свой собственный подраздел в разделе HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*версии*> \Projects\\{} \< *ProjectGUID*>} \Filters\\<*подраздел*>. Имя подраздела может быть произвольным. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] игнорирует имя подраздела и использует только его значения.

 Вы можете управлять контексты, в которых используется фильтр по установке флагов, показано в следующей таблице. Если фильтр не содержит все флаги, установленные, оно будет отображаться после распространенных фильтров в **добавить существующий элемент** диалоговое окно и **открыть файл** диалоговое окно, но он не будет использоваться в **поиск в файлах**  диалоговое окно.

```
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]
@="#3"
"CommonOpenFilesFilter"=dword:00000000
"CommonFindFilesFilter"=dword:00000000
"FindInFilesFilter"=dword:00000000
"NotOpenFileFilter"=dword:00000000
"NotAddExistingItemFilter"=dword:00000000
"SortPriority"=dword:00000064
```

|name|Тип|Описание|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Создает фильтр, один из распространенных фильтров в **поиск в файлах** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, которые не помечены как распространенные.|
|CommonOpenFilesFilter|REG_DWORD|Создает фильтр, один из распространенных фильтров в **открыть файл** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, которые не помечены как распространенные.|
|FindInFilesFilter|REG_DWORD|Приведен фильтр после распространенных фильтров в **поиск в файлах** диалоговое окно.|
|NotOpenFileFilter|REG_DWORD|Указывает, что фильтр не используется в **открыть файл** диалоговое окно.|
|NotAddExistingItemFilter|REG_DWORD|Указывает, что фильтр не используется в **добавить существующий элемент** диалоговое окно.|
|SortPriority|REG_DWORD|Задайте SortPriority, определяющую порядок, в котором отображаются фильтры. Большие значения SortPriority объявленных ранее в списке фильтра.|

## <a name="directory-structure"></a>Структура каталогов
 Пакеты VSPackage можно поместить шаблон файлов и папок в любом месте на локальном или удаленном диске, до тех пор, пока расположение регистрируется через интегрированную среду разработки (IDE). Тем не менее для удобства организации, мы рекомендуем следующую структуру каталогов в пути установки продукта.

 \Templates

 \Projects (содержит шаблоны проектов)

 \Applications

 \Components

 \ ...

 \ProjectItems (содержит элементы проекта)

 \Class

 \Form

 \Web страницы

 \HelperFiles (содержит файлы, используемые в элементах проекта многофайловых)

 \WizardFiles

## <a name="see-also"></a>См. также
- [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Локализация приложений](../../ide/localizing-applications.md)
- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)