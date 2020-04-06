---
title: Регистрация проектов и шаблонов элементов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705828"
---
# <a name="registering-project-and-item-templates"></a>Регистрация шаблонов проектов и элементов
Типы проектов должны зарегистрировать каталоги, где расположены шаблоны проекта и элемента проекта. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]использует регистрационную информацию, связанную с типами проектов, чтобы определить, что следует показывать в диалоговом проекте **Add New** и Добавить диалоговые данные **new Item.**

 Для получения дополнительной информации о шаблонах [см.](../../extensibility/internals/adding-project-and-project-item-templates.md)

## <a name="registry-entries-for-projects"></a>Записи регистрации для проектов
 В следующих примерах показаны записи реестра\\<в соответствии с HKEY_LOCAL_MACHINE-Программное обеспечение,Microsoft-VisualStudio*Версия*>. В сопроводительных таблицах объясняются элементы, используемые в примерах.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|name|Тип|Описание|
|----------|----------|-----------------|
|@|REG_SZ|По умолчанию названия проектов такого рода.|
|DisplayName|REG_SZ|Идентификатор ресурса имени, которое будет получено со спутника DLL, зарегистрированного в рамках пакетов.|
|Пакет|REG_SZ|Идентификатор класса пакета, зарегистрированный в пакетах.|
|ПроектШаблонсДир|REG_SZ|Путь по умолчанию файлов шаблона проекта. Файлы шаблонов проекта отображаются в шаблоне **New Project.**|

### <a name="registering-item-templates"></a>Регистрация шаблонов элементов
 Вы должны зарегистрировать каталог, где вы храните шаблоны элементов.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| name | Тип | Описание |
|--------------------------|-----------| - |
| @ | REG_SZ | Идентификатор ресурсов для шаблонов Добавления пункта. |
| ШаблоныДир | REG_SZ | Путь элементов проекта, отображаемых в диалоговом поле для мастера **Добавления нового элемента.** |
| ШаблоныЛокализованныеСубДир | REG_SZ | Идентификатор ресурсов строки, которая называет субдиректорию TemplatesDir, вмещающей локализованные шаблоны. Поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] при их наличии ресурс строки загружается с спутникового DLL, каждый спутник DLL может содержать другое локальное название субдиректоров. |
| СортировкаПриоритет | REG_DWORD | Установите SortPriority, чтобы управлять порядком, в котором шаблоны отображаются в диалоговом окне **Добавления нового элемента.** Более крупные значения SortPriority отображаются ранее в списке шаблонов. |

### <a name="registering-file-filters"></a>Регистрация фильтров файлов
 Дополнительно можно зарегистрировать фильтры, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] которые используются, когда они подсказывают имена файлов. Например, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] фильтр для диалогового окна **Open File:**

 **Визуальные файлы\*C\*' (.cs, .resx,\*.settings,\*.xsd,\*.wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Для поддержки регистрации нескольких фильтров, каждый фильтр зарегистрирован в своем подключке\\под\<HKEY_LOCAL_MACHINE»Software-Microsoft-VisualStudio\\<*Version*>»Проекты »*ProjectGUID*>»Фильтры\\<*Подключили*>. Подключьное имя произвольно; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] игнорирует имя подключаемых и использует только его значения.

 Можно управлять контекстами, в которых фильтр используется, установив флаги, отображаемые в следующей таблице. Если фильтр не имеет каких-либо флагов набор, он будет перечислен после общих фильтров в **добавить существующий элемент** диалогового окна и окно диалога **Open File,** но он не будет использоваться в **найти в файлах** диалоговом поле.

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
|CommonFindFilesFilter|REG_DWORD|Делает фильтр одним из распространенных фильтров в диалоговом поле **«Найти в файлах».** Общие фильтры перечислены в списке фильтров, прежде чем фильтры не помечены как общие.|
|CommonOpenFilesFilter|REG_DWORD|Делает фильтр одним из распространенных фильтров в диалоговом окне **Open File.** Общие фильтры перечислены в списке фильтров, прежде чем фильтры не помечены как общие.|
|FindInFilesFilter|REG_DWORD|Перечисляет фильтр после общих фильтров в диалоговом окне **Поиска в файлах.**|
|NotOpenFileFilter|REG_DWORD|Указывается, что фильтр не используется в диалоговом окне **Open File.**|
|НеaddExistingItemFilter|REG_DWORD|Указывается, что фильтр не используется в диалоговом окне **Добавления.**|
|СортировкаПриоритет|REG_DWORD|Установите SortPriority для управления порядком отображения фильтров. Более крупные значения SortPriority отображаются ранее в списке фильтров.|

## <a name="directory-structure"></a>Структура каталогов
 VSPackages может поместить файлы шаблонов и папки в любом месте на локальном или удаленном диске, если местоположение зарегистрировано через интегрированную среду разработки (IDE). Однако для удобства организации мы рекомендуем следующую структуру каталога под траекторией установки вашего продукта.

 «Шаблоны»

 «Проекты » (содержит шаблоны проекта)

 «Приложения

 Компоненты

 \ ...

 «ProjectItems» (содержит элементы проекта)

 «Класс»

 «Форма

 Страница веб-страницы

 «HelperFiles» (содержит файлы, используемые в многофайлных элементах проекта)

 «ВолшебникФилис»

## <a name="see-also"></a>См. также

- [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Локализация приложений](../../ide/globalizing-and-localizing-applications.md)
- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
