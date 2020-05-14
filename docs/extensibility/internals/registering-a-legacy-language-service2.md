---
title: Регистрация Службы Языка Наследия2 (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705889"
---
# <a name="registering-a-legacy-language-service"></a>Регистрация языковой службы прежних версий
Следующие разделы предоставляют списки записей реестра для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]различных вариантов языковых услуг, доступных в .

 В следующем списке записей реестра, *VS Reg Root* равен HKEY_LOCAL_MACHINE»SOFTWARE-Microsoft-VisualStudio\\*X.Y*, где *X.Y* является [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] номером версии.

## <a name="registry-entries-for-language-service-options"></a>Записи регистрации для вариантов языковых услуг
 Ключ\\*имени* языка VS Reg *Root*«Языки» языковых служб может содержать следующие значения.

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|(по умолчанию)|REG_SZ|*\<GUID>*|GUID языковой службы.|
|ЛангРесид|REG_DWORD|0x0-0xffff|Идентификатор строки ресурса (ResID) для локализованного названия текста языка.|
|Пакет|REG_SZ|*\<GUID>*|GUID of the VSPackage.|
|ShowCompletion|REG_DWORD|0–1|Уточняется, включены ли параметры **завершения заявления** в диалоговом поле **Options.**|
|ShowSmartIndent|REG_DWORD|0–1|Уточняется, включена ли опция выбора **отступа Smart** в диалоговом поле **Options.**|
|ЗапросСтокКноцветы|REG_DWORD|0–1|Уточняется, используются ли пользовательские или по умолчанию цвета для цветовых ключевых слов.|
|ShowHotURLs|REG_DWORD|0–1|Определяет, может ли пользователь щелкать URL-адреса.|
|По умолчанию для негорячих URL-адресов|REG_DWORD|0–1|Укажите начальную настройку для опции **навигации URL-адреса Enable одним щелчком мыши** в диалоговом поле **Options.**|
|По умолчаниюТовставкапространства|REG_DWORD|0–1|Уточняется, есть ли в языковой сервис "вставить пробелы" в качестве опции вкладки по умолчанию.|
|ShowDropdownBarOption|REG_DWORD|0–1|Включает или отсвадает опцию **панели навигации** в диалоговом поле **Options,** который показывает или скрывает **панель Навигации.**|
|Только окно единого кода|REG_DWORD|0–1|Позволяет или отменяет выбор **New Window** в меню **Window** для языковой службы.|
|EnableAdvancedMembersOption|REG_DWORD|0–1|Позволяет или отклоняет настройки диалогового окна **Options** для **Скрытых Расширенных Участников.**|
|поддержка CF_HTML|REG_DWORD|0–1|Уточняется, позволяет ли редактор копировать и внедывать данные HTML.|
|EnableLineNumbersOption|REG_DWORD|0–1|Уточняется, включены ли параметры **номеров строк** в диалоговом поле **Options** для языковой службы.|
|СкрытьРасширенныеЧленыпо умолчанию|REG_DWORD|0–1|Уточняется, скрыты ли расширенные члены, такие как частные поля, в списках завершений.|
|ShowBraceCompletion|REG_DWORD|0–1|Уточняется, включен ли параметр **завершения Brace** в диалоговом поле **Options.**|

### <a name="example"></a>Пример

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Записи регистрации для вариантов языков debugger
 НАЗВАНИЕ языка *VS Reg*Root\\(Языки) Языковые службы *(Debugger*Languages\\*GUID)* может включать в себя следующие значения.

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|(по умолчанию)|REG_SZ|text|Значение по умолчанию можно использовать для документирования имени языка. Имя этого ключа является GUID оценщика выражения, который * \< *имеет соответствующую запись в VS Reg Root>«AD7Metrics»Expression evaluator.|

### <a name="example"></a>Пример

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Записи регистрации для вариантов инструментов редактора
 Вы можете добавить ключи реестра под ключом EditorToolsOptions для страниц свойств и узлов свойств. Эти ключи и их значения идентифицируют страницы свойств в диалоговом поле **Options** (в меню **Инструментов),** которые используются для настройки языковой службы. В следующем примере *имя страницы —* это имя страницы свойств, а *имя узла* — имя узла в дереве в диалоговом поле **«Параметры».** Вход страницы и вход узла должны быть указаны отдельно.

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|(по умолчанию)|REG_SZ|ResID|Локализованное имя отображения этой страницы опциона. Имя может быть буквальным текстом, или q`nnn`, где `nnn` идентификатор ресурса шнура в спутнике DLL указанного VSPackage.|
|Пакет|REG_SZ|*Guid*|GUID VSPackage, который реализует эту страницу опций.|
|Страница|REG_SZ|*Guid*|GUID страницы свойств, чтобы запросить от <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSPackage, позвонив в метод. Если эта запись реестра отсутствует, ключ реестра описывает узел, а не страницу.|

### <a name="example"></a>Пример

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Записи реестра для вариантов расширения имени файла
 Запись для расширения файла должна включать в себя ведущий период, например ".myext".

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|(по умолчанию)|REG_SZ|*Guid*|Служба GUID для языковой службы по умолчанию для этого типа расширения имени файла.|

### <a name="example"></a>Пример

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Записи регистрации для вариантов редактора
 Ключ *VS Reg Root*может содержать следующие значения:

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|(по умолчанию)|REG_SZ|""|Неиспользованные; Вы можете поместить свое имя здесь для документации.|
|DefaultToolboxTab|REG_SZ|""|Название вкладки ящика инструментов, чтобы сделать по умолчанию, когда редактор активен.|
|DisplayName|REG_SZ|ResID|Имя для отображения в **поле Open With** dialog. Имя — это идентификатор ресурса строки или имя в стандартном формате.|
|ExcludeDefTextEditor|REG_DWORD|0–1|Используется для команды **Open With** Menu. Если вы не хотите усыплять текстовый редактор по умолчанию в списке доступных редакторов для определенного типа файлов, установите это значение до 1.|
|СвязанныеEditorGUID|REG_SZ|*\<GUID>*|Используется для любой языковой службы, которая может открыть файл с поддержкой кодовой страницы. Например, при открытии файла .txt с помощью команды **Open With** предусмотрены варианты использования редактора исходного кода с кодированием и без такового.<br /><br /> GUID, указанный в названии подключаемого ключа, предназначен для фабрики редактора кодовых страниц; связанная GUID, указанная в данном конкретном реестре, предназначена для обычной фабрики редакторов. Цель этой записи заключается в том, что если IDE не открывает файл с помощью редактора по умолчанию, IDE попытается использовать следующий редактор в списке. Этот следующий редактор не должен быть фабрикой редактора codepage, потому что эта фабрика редакторов в основном такая же, как фабрика редакторов, которая потерпела неудачу.|
|Пакет|REG_SZ|*\<GUID>*|VSPackage GUID для ResID отображения.|

### <a name="example"></a>Пример

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Записи регистрации для вариантов логического представления
 *Интерфейс редактора*\\VS Reg Root *>* ключ «LogicalViews» может содержать следующие значения.

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|(по умолчанию)|REG_SZ||Не используется.|
|*\<GUID>*|REG_SZ|""|Ключ к логическим мнениям поддерживается. Вы можете иметь столько из них, как вам нужно. Главное название регистрации, а не значение, которое всегда является пустой строкой.|

### <a name="example"></a>Пример

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Записи регистрации для вариантов расширения редактора
 Ключ *«Расширения» VS Reg Root*«Редактор»,\\*Editor GUID*может содержать следующие значения. Расширение имени файла не включает в себя ведущий период.

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|(по умолчанию)|REG_SZ||Не используется.|
|*\<ext>*|REG_DWORD|0-0xffffffffff|Относительный приоритет расширений. Если два или более языков имеют одно и то же расширение, выбирается язык с более высоким приоритетом.|

 Кроме того, текущий выбор пользователя по умолчанию для редактора хранится\\в HKEY_Current_User»Software/Microsoft/VisualStudio*X.Y*«Редакторы\\по умолчанию*ext*. GUID выбранного языкового сервиса находится в пользовательской записи. Это имеет приоритет для текущего пользователя.

### <a name="example"></a>Пример

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Записи реестра для вариантов управляемого пакета рамочных языковых услуг
 Следующие записи реестра специфичны для классов языковых услуг управляемого пакета (MPF). Эти записи реестра указывают на поддержку в языковой службе для различных функций IntelliSense и для других расширенных функций редактирования.

 Эти записи реестра доступны <xref:Microsoft.VisualStudio.Package.LanguagePreferences> через класс.

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0–1|Поддержка операций IntelliSense.|
|MatchBraces|REG_DWORD|0–1|Поддержка соответствующих языковых пар, таких как скобки, скобки и скобки.|
|Краткие сведения|REG_DWORD|0–1|Поддержка операции IntelliSense Быстрая информация.|
|ShowMatchingBrace|REG_DWORD|0–1|Поддержка отображения соответствующей языковой пары в панели статуса.|
|MatchBracesAtCaret|REG_DWORD|0–1|Поддержка отображения соответствующих языковых пар, как правило, путем выделения двух элементов.|
|MaxErrorСообщения|REG_DWORD|От 0 до n|Максимальное количество ошибок, которые могут быть отображены в окне **списка ошибок.**|
|CodeSenseDelay|REG_DWORD|От 0 до n|Количество миллисекунд, чтобы задержать сярприг перед началом любого фонового разбора для операции IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0–1|Поддержка фонового разбора.|
|ВключитьКомментарий|REG_DWORD|0–1|Поддержка комментариев из выбранных блоков текста, а также подразумевает поддержку некомментируя выбранный текст.|
|EnableFormatВыбор|REG_DWORD|0–1|Поддержка форматирования текста, такого как автоматическое отрезок и регулировка положения брекетов.|
|АвтоАутлипод|REG_DWORD|0–1|Поддержка изложения (регионы, которые могут быть разрушены).|
|МаксРегионы|REG_DWORD|От 0 до n|Максимальное количество скрытых областей на файл.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
