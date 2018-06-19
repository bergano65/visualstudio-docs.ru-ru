---
title: Регистрация прежних версий языка Service2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cb7750f55bd9175c552aa765d21b1334f5f1dfe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134143"
---
# <a name="registering-a-legacy-language-service"></a>Регистрация службы языка для прежних версий
В следующих разделах содержатся списков записей реестра для языка, различные параметры службы, доступные в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 В следующем списке записей реестра *корневой раздел реестра VS* равен HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, где *X.Y* — [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] номер версии.  
  
## <a name="registry-entries-for-language-service-options"></a>Записи реестра для службы параметры языка  
 *Корневой раздел реестра VS*службы \Languages\Language\\*название языка* ключ может содержать следующие значения.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID языковой службы.|  
|LangResID|REG_DWORD|0x0 — 0xffff.|Строковый идентификатор ресурса (ResID) для имени локализованный текст языка.|  
|Пакет|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID пакета VSPackage.|  
|ShowCompletion|REG_DWORD|0—1|Указывает ли **завершение операторов** параметры в **параметры** включены диалоговое окно.|  
|ShowSmartIndent|REG_DWORD|0—1|Указывает ли параметр, чтобы выбрать **смарт-** отступов в **параметры** включен диалоговое окно.|  
|RequestStockColors|REG_DWORD|0—1|Указывает ли пользовательские или цвета по умолчанию используются для закрашивания ключевые слова.|  
|ShowHotURLs|REG_DWORD|0—1|Указывает, является ли пользователь может щелкнуть URL-адреса.|  
|Значение по умолчанию не горячей URL-адреса|REG_DWORD|0—1|Указывает начальный параметр для **включить URL-адреса одним щелчком** в диалоговом окне **параметры** диалоговое окно.|  
|DefaultToInsertSpaces|REG_DWORD|0—1|Указывает, имеет ли языковой службы «вставлять пробелы» как его параметр вкладку по умолчанию.|  
|ShowDropdownBarOption|REG_DWORD|0—1|Включает или отключает **панель навигации** в диалоговом окне **параметры** диалоговым окном, которое показывает или скрывает **панель навигации**.|  
|Только окно кода|REG_DWORD|0—1|Включает или отключает **новое окно** choice в **окна** меню языковой службы.|  
|EnableAdvancedMembersOption|REG_DWORD|0—1|Включает или отключает **параметры** параметра диалогового окна для **Скрывать дополнительные члены**.|  
|Поддержка CF_HTML|REG_DWORD|0—1|Указывает, включает ли редактор копирования и вставки данных HTML.|  
|EnableLineNumbersOption|REG_DWORD|0—1|Указывает ли **номера строк** параметры в **параметры** диалоговое окно включения для языковой службы.|  
|HideAdvancedMembersByDefault|REG_DWORD|0—1|Указывает, будут ли дополнительные члены, такие как закрытые поля скрыты в списках завершения.|  
|ShowBraceCompletion|REG_DWORD|0—1|Указывает ли **фигурную скобку завершения** в диалоговом окне **параметры** включен диалоговое окно.|  
  
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
  
## <a name="registry-entries-for-debugger-languages-options"></a>Записи реестра для языков параметры отладчика  
 *Корневой раздел реестра VS*службы \Languages\Language\\*название языка*\Debugger языков\\*GUID*\ ключ может содержать следующие значения.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|текст|Значение по умолчанию можно использовать для документирования имя языка. Этот ключ называется GUID вычислитель выражений с соответствующей записи в  *\<корневой раздел реестра VS >* \AD7Metrics\Expression оценки.|  
  
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
  
## <a name="registry-entries-for-editor-tools-options"></a>Записи реестра для параметров редакторов  
 Можно добавить разделов реестра в разделе EditorToolsOptions для страниц свойств и свойств узлов. Эти ключи и их значения идентификации страницы свойств в **параметры** диалоговое окно «» (на **средства** меню), которые используются для настройки службы языка. В следующем примере *имя страницы* имя страницу свойств и *имя узла* — это имя узла в дереве на **параметры** диалоговое окно. Запись страниц и запись узла необходимо указать отдельно.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|Идентификатор ресурса|Локализованное отображаемое имя этой страницы параметров. Имя может быть литерального текста или #`nnn`, где `nnn` имеет идентификатор строкового ресурса из вспомогательной библиотеки DLL из указанного пакета VSPackage.|  
|Пакет|REG_SZ|*GUID*|Идентификатор GUID пакета VSPackage, реализующий странице "Параметры".|  
|Страница|REG_SZ|*GUID*|Идентификатор GUID страницы свойств для запроса из пакета VSPackage, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод. Если этот параметр реестра не существует, раздел реестра описание узла, не страницы.|  
  
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
  
## <a name="registry-entries-for-file-name-extension-options"></a>Записи реестра для параметров расширения имени файла  
 Операция для расширения файла следует включить точку в начале, например «.myext».  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|*GUID*|Идентификатор GUID службы служба языка по умолчанию для этого типа расширения имени файла.|  
  
### <a name="example"></a>Пример  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Записи реестра для параметров редактора  
 *Корневой раздел реестра VS*\Editors ключ может содержать следующие значения:  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|""|Не используется; можно поместить здесь ваше имя для документации.|  
|DefaultToolboxTab|REG_SZ|""|Имя вкладки панели элементов, чтобы сделать по умолчанию при активном редакторе.|  
|DisplayName|REG_SZ|Идентификатор ресурса|Имя, отображаемое в **открыть с помощью** диалоговое окно. Оно идентификатор строкового ресурса или имя в стандартном формате.|  
|ExcludeDefTextEditor|REG_DWORD|0—1|Используется для **открыть с помощью** команду меню. Если вы не хотите список текстовом редакторе по умолчанию в списке доступных редакторов для файлов определенного типа, это значение равно 1.|  
|LinkedEditorGUID|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Используется для любой службы языка, можно открыть файл с поддержкой кодовых страниц. Например, при открытии txt-файл с помощью **открыть с помощью** команды предоставляются параметры для использования редактора исходного кода с и без кодирования.<br /><br /> Идентификатор GUID, указано имя подраздела — фабрики редакторов кодовой страницы; связанный идентификатор GUID, указанный в этой записи реестра — Редактор регулярных фабрики. Эта запись предназначен, если интегрированная среда разработки не удается открыть файл с помощью редактора по умолчанию, интегрированной среды разработки будет пытаться использовать следующему редактору в списке. Этот редактор Далее не должно быть фабрики редакторов кодовой страницы из-за этой фабрики редактора аналогична фабрики редакторов, завершившегося ошибкой.|  
|Пакет|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID пакета VSPackage ResID отображаемое имя.|  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>Записи реестра для параметров логическое представление  
 *Корневой раздел реестра VS*\Editors\\*графического пользовательского интерфейса редактора >* \LogicalViews ключ может содержать следующие значения.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ||Не используется.|  
|*\<ИДЕНТИФИКАТОР GUID &GT;*|REG_SZ|""|Ключ для логического представления, которые поддерживаются. При необходимости может иметь как многие из них. Имя записи реестра — важно, не значение, которое всегда является пустой строкой.|  
  
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
  
## <a name="registry-entries-for-editor-extension-options"></a>Записи реестра для параметров расширение редактора  
 *Корневой раздел реестра VS*\Editors\\*GUID редактор*\Extensions ключ может содержать следующие значения. Расширение имени файла не включает точку в начале.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ||Не используется.|  
|*\<Ext >*|REG_DWORD|0-0xffffffff.|Относительный приоритет расширения. Если два или более языки используют то же самое расширение, выбирается язык более высокий приоритет.|  
  
 Кроме того, выбор по умолчанию текущего пользователя для редактора хранится в HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default редакторы\\*ext*. GUID службы, выбранный язык — в пользовательские записи. Это имеет приоритет для текущего пользователя.  
  
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
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Записи реестра для параметров службы языка Managed Package Framework  
 Классы managed package framework (MPF) языка службы зависят следующие параметры реестра. Эти записи реестра указать поддержку в службе языка для различных функций IntelliSense и другие дополнительные возможности редактирования.  
  
 Эти записи реестра осуществляется через <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0—1|Поддержка операций IntelliSense.|  
|MatchBraces|REG_DWORD|0—1|Поддержка сопоставления пары языков, таких как фигурные скобки, круглые и квадратные скобки.|  
|Краткие сведения|REG_DWORD|0—1|Поддержка операции кратких сведений IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0—1|Поддержка отображения соответствующей пары языка в строке состояния.|  
|MatchBracesAtCaret|REG_DWORD|0—1|Поддержка для отображения соответствующих пар языка, обычно через Выделение двух элементов.|  
|MaxErrorMessages|REG_DWORD|от 0 до n|Максимальное число ошибок, которые могут быть отображены в **список ошибок** окна.|  
|CodeSenseDelay|REG_DWORD|от 0 до n|Число миллисекунд, перед запуском фоновые синтаксического анализа для операции IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0—1|Поддержка фоновый синтаксический анализ.|  
|EnableCommenting|REG_DWORD|0—1|Поддержка преобразуйте выбранные блоки текста, а также подразумевает поддержку идет раскомментирование выбранного текста.|  
|EnableFormatSelection|REG_DWORD|0—1|Поддержка форматирования текста, например автоматического отступа или настроить положение фигурных скобок.|  
|AutoOutlining|REG_DWORD|0—1|Поддержка (областей, которые могут быть свернуты) структуры.|  
|MaxRegions|REG_DWORD|от 0 до n|Максимальное число скрытых областей каждого файла.|  
  
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
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)