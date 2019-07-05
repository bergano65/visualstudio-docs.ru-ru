---
title: Поддержка пользовательских параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90f04d5657fb6f680139ee6de5a47625304b5dbd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309758"
---
# <a name="support-for-user-settings"></a>Поддержка параметров пользователя
VSPackage может определять одну или несколько категорий параметров, которые представляют собой группы переменных состояния, которые сохраняются, когда пользователь выбирает **параметры импорта и экспорта** команды **средства** меню. Чтобы включить этот сохраняемость, используйте API параметров в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 Запись реестра, который называется точки настраиваемых параметров и GUID определяет категорию параметров VSPackage. VSPackage может поддерживать несколько категорий параметров, каждый из которых определяется точки настраиваемых параметров.

- Реализации параметров, которые основаны на сборки взаимодействия (с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> интерфейс) необходимо создать точки настраиваемых параметров путем редактирования реестра или с помощью скрипта регистратора (RGS-файл). Для получения дополнительной информации см. [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Код, использующий Managed Package Framework (MPF) необходимо создать точках настраиваемых параметров, подключив <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> объекту VSPackage для каждой точки настраиваемых параметров.

     Если один пакет VSPackage поддерживает несколько точках настраиваемых параметров, каждой точки настраиваемых параметров реализуется отдельный класс и каждый регистрируется с уникальный экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса. Следовательно параметры, реализация класса может поддерживать более чем одной категории параметров.

## <a name="custom-settings-point-registry-entry-details"></a>Подробные сведения о записи реестра точки настраиваемых параметров
 Точках настраиваемых параметров создаются в записи реестра в следующем расположении: HKLM\Software\Microsoft\VisualStudio\\ *\<версии >* \UserSettings\\`<CSPName>`, где `<CSPName>` поддерживает VSPackage — это имя точки настраиваемых параметров и  *\<версии >* — это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], например 8.0.

> [!NOTE]
> Путь к корневому каталогу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<версии >* может быть переопределено с помощью альтернативного корневой при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки (IDE) инициализирован. Дополнительные сведения см. в разделе [переключателей командной строки](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Структура записи реестра как показано ниже:

 HKLM\Software\Microsoft\VisualStudio\\ *\<Version>* \UserSettings\

 `<CSPName`> = «#12345"s

 Пакет = «{XXXXXX XXXX XXXX XXXX XXXXXXXXX}»

 Категория = «{гггг ГГГГГГ гггг гггг YYYYYYYYY}»

 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'

 AlternateParent = CategoryName

| name | Тип | Данные | Описание |
|-----------------|--------| - | - |
| (Значение по умолчанию) | REG_SZ | Имя точки настраиваемых параметров | Имя раздела, `<CSPName`>, нелокализованное имя точки настраиваемых параметров.<br /><br /> Для реализации в зависимости от MPF, его название получается путем объединения `categoryName` и `objectName` аргументы <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктор в `categoryName_objectName`.<br /><br /> Ключ может быть пустым или может содержать идентификатор ссылки для локализованной строки в вспомогательной библиотеке DLL. Это значение получается из `objectNameResourceID` аргумент <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктор. |
| Пакет | REG_SZ | Идентификатор GUID | Идентификатор GUID VSPackage, который реализует точки настраиваемых параметров.<br /><br /> Реализации исходя из с помощью MPF <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> , используйте конструктор `objectType` аргументу, содержащему VSPackage <xref:System.Type> и отражение для получения этого значения. |
| Категория | REG_SZ | Идентификатор GUID | Идентификатор GUID, определяющий категорию параметров.<br /><br /> Для реализации в зависимости от сборок взаимодействия, это значение может быть произвольно выбранным GUID, который [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] передает IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> методы. Все реализации этих двух методов следует проверить их аргументов GUID.<br /><br /> Для реализации в зависимости от MPF, полученных этим идентификатором GUID <xref:System.Type> класса, реализующего [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] механизм параметров. |
| ResourcePackage | REG_SZ | Идентификатор GUID | Необязательный параметр.<br /><br /> Путь к вспомогательной DLL которого содержит локализованные строки, если реализации VSPackage не поддерживает их.<br /><br /> MPF использует отражение для получения необходимого ресурса VSPackage, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса не устанавливает этот аргумент. |
| AlternateParent | REG_SZ | Имя папки в разделе Сервис-Параметры страницы, содержащей этот точки настраиваемых параметров. | Необязательный параметр.<br /><br /> Это значение необходимо задать только в том случае, если параметры реализация поддерживает **Сервис-Параметры** страниц, использующих механизм сохранения в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] вместо механизма в модели автоматизации для сохранения состояния.<br /><br /> В этом случае — значение в ключе AlternateParent `topic` раздел `topic.sub-topic` строку, используемую для определения специального **ToolsOptions** страницы. Например, для **ToolsOptions** страницы `"TextEditor.Basic"` AlternateParent малейший `"TextEditor"`.<br /><br /> Когда <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> создает точки настраиваемых параметров, он совпадает со значением имя категории. |
