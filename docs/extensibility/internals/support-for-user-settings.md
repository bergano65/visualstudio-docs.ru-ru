---
title: Поддержка настроек пользователя Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704780"
---
# <a name="support-for-user-settings"></a>Поддержка параметров пользователя
VSPackage может определить одну или несколько категорий параметров, которые представляют собой группы переменных состояния, которые сохраняются, когда пользователь выбирает команду **«Настройки импорта/экспорта»** в меню **«Инструменты».** Для обеспечения такой настойчивости используются настройки [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]AIS в .

 Запись реестра, которая называется точкой пользовательских настроек, и GUID определяет категорию настроек VSPackage. VSPackage может поддерживать несколько категорий настроек, каждая из которых определена точкой пользовательских настроек.

- Реализация настроек, основанных на межопомневных <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> сборках (с использованием интерфейса), должна создавать пользовательские настройки, либо редактируя реестр, либо используя скрипт регистратора (файл.rgs). Для получения дополнительной информации см. [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Код, который использует рамочную программу управляемого пакета (MPF), должен создавать пользовательские настройки, прикрепляя <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> к VSPackage для каждого пункта пользовательских настроек.

     Если один VSPackage поддерживает несколько пользовательских точек настройки, каждая точка пользовательских настроек <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> реализуется отдельным классом, и каждая зарегистрирована уникальным экземпляром класса. Следовательно, класс реализации параметров может поддерживать несколько категорий параметров.

## <a name="custom-settings-point-registry-entry-details"></a>Пользовательские настройки точки регистрации Сведения
 Пользовательские настройки Очки создаются в регистрации запись в следующем месте:\\*\< *HKLM-Software-Microsoft-VisualStudio Версия>"UserSettings\\`<CSPName>`, где `<CSPName>` это имя пользовательских настроек точки VSPackage поддерживает и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] * \<версия>* является версия , например, 8.0.

> [!NOTE]
> Корневой путь HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio\\*\<Version>* может быть перекрыт [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с альтернативным корнем при инициализации интегрированной среды разработки (IDE). Для получения дополнительной информации [см.](../../extensibility/command-line-switches-visual-studio-sdk.md)

 Структура регистрации иллюстрируется ниже:

 HKLM-Программное обеспечение,Microsoft-VisualStudio\\*\<версия>*«UserSettings»

 `<CSPName`>и "#12345"

 Пакет : «XXXXXX XXXX XXXX XXXXXXXXXXXXXXХ) »

 Категория : «Yyyyy yyy yyy yyy yyy yyyyyyyyyyyyy'

 Ресурсный пакет - «Я»

 АльтернативныйРодитель - КатегорияИмя

| name | Type | Данные | Описание |
|-----------------|--------| - | - |
| (по умолчанию) | REG_SZ | Название точки пользовательских настроек | Имя ключа, `<CSPName`>, является нелокализованным названием точки пользовательских настроек.<br /><br /> Для реализаций, основанных на MPF, имя ключа `categoryName` получается путем <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> объединения `categoryName_objectName`и `objectName` аргументов конструктора в .<br /><br /> Ключ может быть пустым, или он может содержать идентификатор ссылки на локализованную строку в спутниковой DLL. Это значение получено `objectNameResourceID` от аргумента к конструктору. <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> |
| Пакет | REG_SZ | GUID | GUID VSPackage, который реализует точку пользовательских настроек.<br /><br /> Реализации, основанные на <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> MPF с использованием `objectType` класса, использовать аргумент <xref:System.Type> конструктора, содержащий VSPackage и отражение, чтобы получить это значение. |
| Категория | REG_SZ | GUID | GUID определяет категорию настроек.<br /><br /> Для реализаций, основанных на межопомненных сборках, это значение может [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] быть произвольно выбранным GUID, который IDE передает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> методам. Все реализации этих двух методов должны проверить свои аргументы GUID.<br /><br /> Для реализаций, основанных на MPF, этот <xref:System.Type> GUID получается [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] классом, реализующим механизм настроек. |
| РесурсНыйпакет | REG_SZ | GUID | Необязательный параметр.<br /><br /> Путь к спутнику DLL, содержащему локализованные строки, если реализация VSPackage не поставляет их.<br /><br /> MPF использует отражение для получения правильного <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> ресурса VSPackage, поэтому класс не устанавливает этот аргумент. |
| Альтернативныйродитель | REG_SZ | Название папки под страницей Параметры инструментов, содержащей эту точку пользовательских настроек. | Необязательный параметр.<br /><br /> Это значение необходимо установить только в том случае, если реализация параметров поддерживает страницы **«Параметры инструментов»,** которые используют механизм сохранения в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] модели автоматизации для сохранения состояния.<br /><br /> В этих случаях значение в ключе `topic` AlternateParent `topic.sub-topic` — это раздел строки, используемый для определения конкретной страницы **ToolsOptions.** Например, для страницы `"TextEditor.Basic"` `"TextEditor"` **ToolsOptions** значение AlternateParent будет .<br /><br /> При <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> создании точки пользовательских настроек она совпадает с именем категории. |
