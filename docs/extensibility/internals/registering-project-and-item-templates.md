---
title: Регистрация шаблонов проектов и элементов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85c22d0191d015979dff5a4845c4dda0af96ee60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="registering-project-and-item-templates"></a>Регистрация шаблонов проектов и элементов
Типы проектов необходимо зарегистрировать каталоги, где находятся их шаблонов проектов и элементов проектов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует сведения о регистрации, связанные с типами проектов, чтобы определить, что для отображения в **Добавление нового проекта** и **Добавление нового элемента** диалоговым окнам.  
  
 Дополнительные сведения о шаблонах см. в разделе [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Записи реестра для проектов  
 В следующих примерах показаны записи реестра в разделе HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*версии*>. В сопутствующей таблицах описываются элементы, используемые в примерах.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|name|Тип|Описание|  
|----------|----------|-----------------|  
|@|REG_SZ|Имя по умолчанию для проектов этого типа.|  
|DisplayName|REG_SZ|Идентификатор ресурса имени должно быть извлечено из вспомогательной библиотеки DLL зарегистрирован пакетов.|  
|Пакет|REG_SZ|Идентификатор класса пакета зарегистрирован пакетов.|  
|ProjectTemplatesDir|REG_SZ|Путь по умолчанию файлы шаблонов проекта. Файлы шаблонов проекта отображаются по **новый проект** шаблона.|  
  
### <a name="registering-item-templates"></a>Регистрация шаблонов элементов  
 Каталог, где хранятся шаблоны элементов, необходимо зарегистрировать.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|name|Тип|Описание|  
|----------|----------|-----------------|  
|@|REG_SZ|Идентификатор ресурса для шаблонов добавить элемент.|  
|TemplatesDir|REG_SZ|Путь проекта элементов, отображаемых в диалоговом окне **Добавление нового элемента** мастера.|  
|TemplatesLocalizedSubDir|REG_SZ|Идентификатор ресурса строки с именем подкаталога TemplatesDir, который содержит локализованных шаблонов. Поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает строковый ресурс из вспомогательные библиотеки DLL при их наличии, каждой вспомогательной библиотеки DLL могут содержать разные локализованные подкаталог с именем.|  
|SortPriority|REG_DWORD|Задать SortPriority, определяющую порядок отображения шаблонов в **Добавление нового элемента** диалоговое окно. Большие значения SortPriority объявленных ранее в списке шаблонов.|  
  
### <a name="registering-file-filters"></a>Регистрация фильтры файлов  
 При необходимости вы можете зарегистрировать фильтры, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует его по запросу для имен файлов. Например [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] фильтрации для **открыть файл** используется диалоговое окно:  
  
 **Файлы Visual C# (\*.cs,\*.resx,\*.settings,\*XSD-файл,\*.wsdl);\*. CS,\*.resx,\*.settings,\*XSD-файл,\*.wsdl)**  
  
 Для поддержки регистрации несколько фильтров, каждый фильтр регистрируется в свой собственный подразделом HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*версии*> \Projects\\{} \< *ProjectGUID*>} \Filters\\<*подраздел*>. Имя раздела реестра может быть произвольным. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] игнорирует имя подраздела и использует только его значения.  
  
 Можно управлять контексты, в которых используется фильтр флаги, показанные в следующей таблице. Если фильтр имеет флаги, установленные, он должен отображаться после общие фильтры в **Добавление существующего элемента** диалоговое окно и **открыть файл** диалоговое окно, но он не будет использоваться в **поиск в файлах**  диалоговое окно.  
  
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
|CommonFindFilesFilter|REG_DWORD|Создает фильтр, один из распространенных фильтров в **поиск в файлах** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, не помечен как общий.|  
|CommonOpenFilesFilter|REG_DWORD|Создает фильтр, один из распространенных фильтров в **открыть файл** диалоговое окно. Общие фильтры, перечислены в списке фильтров перед фильтрами, не помечен как общий.|  
|FindInFilesFilter|REG_DWORD|Перечисляет фильтр после общие фильтры в **поиск в файлах** диалоговое окно.|  
|NotOpenFileFilter|REG_DWORD|Указывает, что фильтр не используется в **открыть файл** диалоговое окно.|  
|NotAddExistingItemFilter|REG_DWORD|Указывает, что фильтр не используется в **Добавление существующего элемента** диалоговое окно.|  
|SortPriority|REG_DWORD|Задать SortPriority для указания порядка, в котором отображаются фильтры. Большие значения SortPriority объявленных ранее в списке фильтров.|  
  
## <a name="directory-structure"></a>Структура каталогов  
 Пакеты VSPackage можно поместить шаблон файлов и папок в любом месте на локальном или удаленном диске, до тех пор, пока зарегистрированы расположение с помощью интегрированной среды разработки (IDE). Однако для упрощения организации, мы рекомендуем следующую структуру каталогов в пути установки продукта.  
  
 \Templates  
  
 \Projects (содержит шаблоны проектов)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (содержит элементы проекта)  
  
 \Class  
  
 \Form  
  
 \Web страницы  
  
 \HelperFiles (содержит файлы, используемые в элементах нескольких файлов проекта)  
  
 \WizardFiles  
  
## <a name="see-also"></a>См. также  
 [Добавление в проект и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Мастеры](../../extensibility/internals/wizards.md)   
 [Локализация приложений](../../ide/localizing-applications.md)   
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)