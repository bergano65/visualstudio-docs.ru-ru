---
title: Регистрация языковой службы прежних версий2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 59fbdb3417bbeb09a47f1c7a7b0552f230a6d269
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563018"
---
# <a name="registering-a-legacy-language-service"></a>Регистрация языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [регистрация языковой службы прежних версий2](https://docs.microsoft.com/visualstudio/extensibility/internals/registering-a-legacy-language-service2).  
  
В следующих разделах приведены списки записей реестра для различные языковые параметры службы, доступные в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 В следующем списке записей реестра *корневой Reg VS* равен HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, где *X.Y* — [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] номер версии.  
  
## <a name="registry-entries-for-language-service-options"></a>Записи реестра для службы параметры языка  
 *Корневой Reg VS*служб \Languages\Language\\*название языка* ключ может содержать следующие значения.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID языковой службы.|  
|LangResID|REG_DWORD|0x0 — 0xffff|Строковый идентификатор ресурсов (идентификатор ресурса) локализованное текстовое имя языка.|  
|Пакет|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID пакета VSPackage.|  
|ShowCompletion|REG_DWORD|0—1|Указывает ли **завершение операторов** параметры в **параметры** включены диалоговое окно.|  
|ShowSmartIndent|REG_DWORD|0—1|Указывает ли возможность выбирать **смарт-** отступов в **параметры** становится доступным поле диалогового окна.|  
|RequestStockColors|REG_DWORD|0—1|Указывает ли пользовательские или цвет ключевые слова используются цвета по умолчанию.|  
|ShowHotURLs|REG_DWORD|0—1|Указывает, является ли пользователь может щелкнуть URL-адреса.|  
|По умолчанию на "Горячий" без URL-адреса|REG_DWORD|0—1|Указывает начальное значение для параметра **включить URL-адреса однократным щелчком** в диалоговом окне **параметры** диалоговое окно.|  
|DefaultToInsertSpaces|REG_DWORD|0—1|Указывает, имеет ли языковая служба «вставлять пробелы» как его параметр вкладку по умолчанию.|  
|ShowDropdownBarOption|REG_DWORD|0—1|Включает или отключает **панель навигации** в диалоговом окне **параметры** диалоговое окно, которое показывает или скрывает **панель навигации**.|  
|Только окно единого кода|REG_DWORD|0—1|Включает или отключает **новое окно** choice в **окно** меню для языковой службы.|  
|EnableAdvancedMembersOption|REG_DWORD|0—1|Включает или отключает **параметры** настройку диалогового окна для **Скрывать дополнительные члены**.|  
|Поддержка CF_HTML|REG_DWORD|0—1|Указывает, включает ли редактор копирования и вставки данных HTML.|  
|EnableLineNumbersOption|REG_DWORD|0—1|Указывает ли **номера строк** параметры в **параметры** диалоговое окно включен для языковой службы.|  
|HideAdvancedMembersByDefault|REG_DWORD|0—1|Указывает, скрыты ли дополнительные члены, такие как закрытые поля в список завершения.|  
|ShowBraceCompletion|REG_DWORD|0—1|Указывает ли **парные фигурные скобки завершения** в диалоговом окне **параметры** становится доступным поле диалогового окна.|  
  
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
 *Корневой Reg VS*служб \Languages\Language\\*название языка*\Debugger языков\\*GUID*\ ключ может содержать следующие значения.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|текст|Значение по умолчанию можно использовать для документирования имя языка. Имя данного ключа представляет собой идентификатор GUID вычислителя выражений с соответствующей записи в  *\<корневой Reg VS >* \AD7Metrics\Expression вычислителя.|  
  
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
  
## <a name="registry-entries-for-editor-tools-options"></a>Записи реестра для редактора Сервис-Параметры  
 Можно добавить разделы реестра в разделе EditorToolsOptions для страницы свойств и свойств узлов. Эти ключи и значения идентификации страниц свойств в **параметры** диалоговое окно (на **средства** меню), которые используются для настройки службы языка. В следующем примере *имя страницы* имя страницы свойств, и *имя узла* — это имя узла в дереве на **параметры** диалоговое окно. Запись страниц и запись узла необходимо указать отдельно.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|Идентификатор ресурса|Локализованное отображаемое имя этой страницы параметра. Имя может быть литерального текста или #`nnn`, где `nnn` является идентификатор строкового ресурса в вспомогательной библиотеке DLL указанного пакета VSPackage.|  
|Пакет|REG_SZ|*GUID*|Идентификатор GUID VSPackage, который реализует странице "Параметры".|  
|Страница|REG_SZ|*GUID*|Идентификатор GUID страницы свойств для запроса из VSPackage, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод. Если этот параметр реестра отсутствует, раздел реестра описывает узел, не страница.|  
  
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
 Операция для расширения файла должен включать точку в начале, например «.myext».  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|*GUID*|Идентификатор GUID службы для службы языка по умолчанию для этого типа расширения имени файла.|  
  
### <a name="example"></a>Пример  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Записи реестра для параметров редактора  
 *Корневой Reg VS*\Editors ключ может содержать следующие значения:  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|""|Не используется; Вы можете поместить название своей документации.|  
|DefaultToolboxTab|REG_SZ|""|Имя вкладки панели элементов, чтобы сделать значением по умолчанию при активном редакторе.|  
|DisplayName|REG_SZ|Идентификатор ресурса|Имя, отображаемое в **открыть с помощью** диалоговое окно. Имя — это идентификатор строкового ресурса или имя в стандартном формате.|  
|ExcludeDefTextEditor|REG_DWORD|0—1|Используется для **открыть с помощью** команды меню. Если вы не хотите списке текстового редактора по умолчанию в список доступных редакторов для файлов определенного типа, это значение равно 1.|  
|LinkedEditorGUID|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Используется для служб языка, которые можно открыть файл с поддержкой кодовой страницы. Например, при открытии txt-файл с помощью **открыть с помощью** команды предоставляются параметры для использования редактора исходного кода с и без кодирования.<br /><br /> Идентификатор GUID, указанный имя подраздела — для фабрики редактора кодовая страница; связанный идентификатор GUID, указанный в этой записи реестра — Редактор регулярных фабрики. Цель этой записи — что если интегрированной среды разработки открывается файл с помощью редактора по умолчанию, интегрированная среда разработки будет пытаться использовать следующий редактор в списке. Это следующий редактор не должно быть фабрики редактора кодовую страницу, так как этой фабрикой редактора по сути совпадает фабрики редактора, не удалось.|  
|Пакет|REG_SZ|*\<ИДЕНТИФИКАТОР GUID &GT;*|Идентификатор GUID VSPackage ResID отображаемое имя.|  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>Записи реестра для логического представления параметров  
 *Корневой Reg VS*\Editors\\*графического пользовательского интерфейса редактора >* \LogicalViews ключ может содержать следующие значения.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ||Не используется.|  
|*\<ИДЕНТИФИКАТОР GUID &GT;*|REG_SZ|""|Ключ для логического представления, поддерживаемые. Может иметь как многие из них, как требуется. Имя записи реестра — это том, что важно не значение, которое всегда является пустой строкой.|  
  
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
  
## <a name="registry-entries-for-editor-extension-options"></a>Записи реестра для параметров расширения редактора  
 *Корневой Reg VS*\Editors\\*GUID редактора*\Extensions ключ может содержать следующие значения. Расширение имени файла не включает точку в начале.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|(Значение по умолчанию)|REG_SZ||Не используется.|  
|*\<Ext >*|REG_DWORD|0 — 0xffffffff|Относительный приоритет расширения. Если два или несколько языков, используют то же самое расширение, выбирать язык более высоким приоритетом.|  
  
 Кроме того, по умолчанию текущего пользователя для редактора хранится в HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default редакторы\\*ext*. Идентификатор GUID службы, выбранный язык находится в элемент Custom. Имеет приоритет для текущего пользователя.  
  
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
 Следующие записи реестра относятся только к классы управляемых пакетов framework (MPF) языковой службы. Эти записи реестра указать поддержку в службе языка для различных функций IntelliSense и другие дополнительные возможности редактирования.  
  
 Эти записи реестра осуществляется через <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0—1|Поддержка операции IntelliSense.|  
|MatchBraces|REG_DWORD|0—1|Поддержка сопоставление языковых пар, таких как фигурные скобки, круглые и квадратные скобки.|  
|Краткие сведения|REG_DWORD|0—1|Поддержка операции краткие сведения IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0—1|Поддержка отображения соответствующая языковая пара в строке состояния.|  
|MatchBracesAtCaret|REG_DWORD|0—1|Поддержка отображения соответствующие языковые пары, обычно с помощью выделения два элемента.|  
|MaxErrorMessages|REG_DWORD|0-n|Максимальное количество ошибок, которые могут отображаться в **список ошибок** окна.|  
|CodeSenseDelay|REG_DWORD|0-n|Количество миллисекунд, перед запуском фоновые синтаксического анализа для операции IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0—1|Поддержка фоновый синтаксический анализ.|  
|EnableCommenting|REG_DWORD|0—1|Поддержка комментирования выбранные блоки текста, а также подразумевает поддержку раскомментирование выбранного текста.|  
|EnableFormatSelection|REG_DWORD|0—1|Поддержка форматирования текста, такие как автоматические отступы или изменить положение фигурных скобок.|  
|AutoOutlining|REG_DWORD|0—1|Поддержка (областей, которые можно свернуть) структуры.|  
|MaxRegions|REG_DWORD|0-n|Максимальное количество скрытых областей каждого файла.|  
  
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

