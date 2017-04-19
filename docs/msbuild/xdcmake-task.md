---
title: "Задача XDCMake | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 491786ecc75c3a396098d434e58e4f6635a3844c
ms.lasthandoff: 04/05/2017

---
# <a name="xdcmake-task"></a>Задача XDCMake
Является оболочкой для средства XML-документации (xdcmake.exe), которая помещает в XML-файл файлы комментариев (XDC-файлы) для документа XML.  
  
 XDC-файл создается, если ввести комментарии к документации в исходный код Visual C++ и выполнить компиляцию с использованием параметра компиляции [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Дополнительные сведения см. в разделах [Справочник по XDCMake](/cpp/ide/xdcmake-reference), [Страницы свойств средства создания XML-документов](/cpp/ide/xml-document-generator-tool-property-pages), а также в разделе справки, вызываемом с помощью параметра командной строки (**/?**) для файла xdcmake.exe.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию средство xdcmake.exe поддерживает несколько параметров командной строки. Для поддержки дополнительных параметров необходимо указать параметр командной строки **/old**.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описываются параметры задачи **XDCMake**.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Необязательный параметр типа **String[]**.<br /><br /> Указывает один или несколько дополнительных XDC-файлов для слияния.<br /><br /> Дополнительные сведения см. в описании параметра **Дополнительные файлы документации** в разделе [Страницы свойств средства создания XML-документов](/cpp/ide/xml-document-generator-tool-property-pages). Также см. описание параметров командной строки **/old** и **/Fs** для файла xdcmake.exe.|  
|**AdditionalOptions**|Необязательный параметр типа **String**.<br /><br /> Список параметров, как указано в командной строке. Например, "*/параметр1 /параметр2 /параметр#*". Этот параметр используется для указания параметров, не представленных каким-либо другим параметром задачи **XDCMake**.<br /><br /> Дополнительные сведения см. в разделах [Справочник по XDCMake](/cpp/ide/xdcmake-reference), [Страницы свойств средства создания XML-документов](/cpp/ide/xml-document-generator-tool-property-pages), а также в разделе справки, вызываемом с помощью параметра командной строки (**/?**) для файла xdcmake.exe.|  
|**DocumentLibraryDependencies**|Необязательный параметр типа **Boolean**.<br /><br /> Если имеет значение `true` и текущий проект содержит зависимости от проекта статической библиотеки (.lib) в решении, XDC-файлы для такого проекта библиотеки включаются в выходной XML-файл для текущего проекта.<br /><br /> Дополнительные сведения см. в описании параметра **Зависимости библиотек документов** в разделе [Страницы свойств средства создания XML-документов](/cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Необязательный параметр типа **String**.<br /><br /> Переопределяет имя выходного файла по умолчанию. Имя по умолчанию является производным от имени первого обработанного XDC-файла.<br /><br /> Дополнительные сведения см. в описании параметра **/out:**`filename` в разделе [Справочник по XDCMake](/cpp/ide/xdcmake-reference). Также см. описание параметров командной строки **/old** и **/Fo** для файла xdcmake.exe.|  
|**ProjectName**|Необязательный параметр типа **String**.<br /><br /> Имя текущего проекта.|  
|**SlashOld**|Необязательный параметр типа **Boolean**.<br /><br /> Если имеет значение `true`, могут использоваться дополнительные параметры для xdcmake.exe.<br /><br /> Дополнительные сведения см. в описании параметра командной строки **/old** для xdcmake.exe.|  
|**Sources**|Обязательный параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.|  
|**SuppressStartupBanner**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/nologo** в разделе [Справочник по XDCMake](/cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Необязательный параметр типа **String**.<br /><br /> Задает каталог для журнала отслеживания.|  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
