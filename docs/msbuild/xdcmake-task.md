---
title: Задача XDCMake | Документы Майкрософт
description: Узнайте, как MSBuild использует задачу XDCMake для создания оболочки для средства xdcmake.exe документации XML, которое объединяет файлы комментариев документации XML в файл .xml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a867146d48b5ba6c4bfb2ac33b45c505b6f6c37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971054"
---
# <a name="xdcmake-task"></a>XDCMake - задача

Является оболочкой для средства XML-документации (*xdcmake.exe*), которая помещает в XML-файл файлы комментариев (*XDC-файлы*) для файла *XML*.

 Файл *XDC* создается при добавлении комментариев к документации в исходный код C++ и выполнении компиляции с использованием параметра компиляции [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Дополнительные сведения см. в разделах [Справочник по XDCMake](/cpp/build/reference/xdcmake-reference), [Страницы свойств средства создания XML-документов](/cpp/build/reference/xml-document-generator-tool-property-pages), а также в разделе справки, вызываемом с помощью параметра командной строки ( **/?** ) для файла *xdcmake.exe*.

## <a name="remarks"></a>Remarks

 По умолчанию средство *xdcmake.exe* поддерживает несколько параметров командной строки. Для поддержки дополнительных параметров необходимо указать параметр командной строки **/old**.

## <a name="parameters"></a>Параметры

 В следующей таблице описываются параметры задачи **XDCMake**.

|Параметр|Description|
|---------------|-----------------|
|**AdditionalDocumentFile**|Необязательный параметр типа **String[]** .<br /><br /> Указывает один или несколько дополнительных файлов *XDC* для слияния.<br /><br /> Дополнительные сведения см. в описании параметра **Дополнительные файлы документации** в разделе [Страницы свойств средства создания XML-документов](/cpp/build/reference/xml-document-generator-tool-property-pages). Также см. описание параметров командной строки **/old** и **/Fs** для файла *xdcmake.exe*.|
|**AdditionalOptions**|Необязательный параметр **String** .<br /><br /> Список параметров, как указано в командной строке. Например, /\<option1> /\<option2> /\<option#>. Этот параметр используется для указания параметров, не представленных каким-либо другим параметром задачи **XDCMake**.<br /><br /> Дополнительные сведения см. в разделах [Справочник по XDCMake](/cpp/build/reference/xdcmake-reference), [Страницы свойств средства создания XML-документов](/cpp/build/reference/xml-document-generator-tool-property-pages), а также в разделе справки, вызываемом с помощью параметра командной строки ( **/?** ) для файла *xdcmake.exe*.|
|**DocumentLibraryDependencies**|Необязательный параметр типа **Boolean**.<br /><br /> Если имеет значение `true` и текущий проект содержит зависимости от проекта статической библиотеки ( *.lib*) в решении, файлы *XDC* для такого проекта библиотеки включаются в выходной файл *XML* для текущего проекта.<br /><br /> Дополнительные сведения см. в описании параметра **Зависимости библиотек документов** в разделе [Страницы свойств средства создания XML-документов](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Необязательный параметр **String** .<br /><br /> Переопределяет имя выходного файла по умолчанию. Имя по умолчанию является производным от имени первого обработанного файла *XDC*.<br /><br /> Дополнительные сведения см. в описании параметра **/out:\<filename>** в разделе [Справочник по XDCMake](/cpp/build/reference/xdcmake-reference). Также см. описание параметров командной строки **/old** и **/Fo** для файла *xdcmake.exe*.|
|**Имя проекта**|Необязательный параметр **String** .<br /><br /> Имя текущего проекта.|
|**SlashOld**|Необязательный параметр типа **Boolean**.<br /><br /> Если имеет значение `true`, могут использоваться дополнительные параметры для *xdcmake.exe*.<br /><br /> Дополнительные сведения см. в описании параметра командной строки **/old** для *xdcmake.exe*.|
|**Источники**|Обязательный параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.|
|**SuppressStartupBanner**|Необязательный параметр **Boolean** .<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/nologo** в разделе [Справочник по XDCMake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Необязательный параметр **String** .<br /><br /> Задает каталог для журнала отслеживания.|

## <a name="see-also"></a>См. также раздел

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)