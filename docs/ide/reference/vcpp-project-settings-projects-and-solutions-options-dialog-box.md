---
title: "Параметры проекта VC++, страница &quot;Проекты и решения&quot;, диалоговое окно &quot;Параметры&quot; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: fbe834e4e8178a129f68cec1c4a78ffea3c9fd7c
ms.lasthandoff: 04/25/2017

---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Параметры проекта VC++, страница "Проекты и решения", диалоговое окно "Параметры"
В этом диалоговом окне можно определять параметры проекта [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], связанные с файлами журналов сборки и другими вспомогательными файлами.  
  
### <a name="to-access-this-dialog-box"></a>Вызов диалогового окна  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  Выберите **Проекты и решения**, а затем **Параметры проекта VC++**.  
  
## <a name="build-customization-search-path"></a>Путь поиска настройки сборки  
 Задает список каталогов, содержащих файлы с расширением Rules, которые определяют правила сборки проектов.  
  
## <a name="build-logging"></a>Журнал сборки  
 **Да**  
 Включает ведение файла журнала сборки. Этот параметр создает файл BuildLog.htm в каталоге временных файлов проекта. После каждой новой сборки файл BuildLog.htm перезаписывается.  
  
 **No**  
 Отключает ведение файла журнала сборки.  
  
## <a name="build-timing"></a>Время сборки  
 **Да**  
 Включает регистрацию времени сборки. Если этот параметр выбран, время, затрачиваемое на выполнение сборки, отображается в окне вывода. Дополнительные сведения см. в разделе [Окно вывода](../../ide/reference/output-window.md).  
  
 **No**  
 Отключает регистрацию времени сборки.  
  
## <a name="extensions-to-hide"></a>Скрываемые расширения  
 Задает расширения файлов, которые не будут отображаться в **обозревателе решений** при выборе параметра **Показать все файлы**.  
  
## <a name="extensions-to-include"></a>Включаемые расширения  
 Задает расширения файлов, которые могут переноситься в проект.  
  
## <a name="maximum-concurrent-c-compilations"></a>Максимум одновременных компиляций C++  
 Задает максимальное число ядер ЦП для параллельной компиляции C++.  
  
## <a name="show-environment-in-log"></a>Отображать среду в журнале  
 **Да**  
 Выводит все переменные среды в файл журнала сборки. Этот параметр задает вывод всех переменных среды во время сборки проектов [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] в файл журнала сборки.  
  
 **No**  
 Исключает переменные среды из файла журнала сборки.  
  
## <a name="solution-explorer-mode"></a>Режим обозревателя решений  
 **Показывать только файлы проекта**  
 В **обозревателе решений** отображаются только файлы проекта.  
  
 **Показывать все файлы**  
 В **обозревателе решений** отображаются файлы проекта, а также файлы из папки проекта на диске.  
  
## <a name="see-also"></a>См. также  
 [Сборка программ C/C++](/cpp/build/building-c-cpp-programs)   
 [Справочные сведения о сборке C/C++](/cpp/build/reference/c-cpp-building-reference)
