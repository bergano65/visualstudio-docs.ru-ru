---
title: "Управление внешними инструментами | Документы Майкрософт"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 1d273749cc41eb975dc9f93329edf9a57aaae09a
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

---
# <a name="manage-external-tools"></a>Управление внешними инструментами
Внешние инструменты можно вызвать прямо из Visual Studio с помощью меню **Сервис**. Несколько инструментов по умолчанию доступны в меню **Сервис**, однако вы можете самостоятельно добавлять другие исполняемые файлы.  

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Инструменты, доступные в меню "Сервис" Visual Studio
 В меню **Сервис** содержится несколько встроенных команд:

*  **Расширения и обновления** для [управления расширениями Visual Studio](finding-and-using-visual-studio-extensions.md).
*  **Диспетчер фрагментов кода...** для [организации фрагментов кода](code-snippets.md#code-snippet-manager).
*  **PreEmptive Protection — Dotfuscator** для запуска [Dotfuscator Community Edition (CE)](dotfuscator/index.md) (если эта программа [установлена](dotfuscator/install.md)).
*  **Настройка...** для [настройки меню и панелей инструментов](how-to-customize-menus-and-toolbars-in-visual-studio.md).
*  **Параметры...** для [установки различных параметров интегрированной среды разработки Visual Studio и других инструментов](reference/options-dialog-box-visual-studio.md).

## <a name="add-new-tools-to-the-tools-menu"></a>Добавление новых инструментов в меню "Сервис" 
 Вы можете добавить внешний инструмент в меню **Сервис**. Откройте диалоговое окно **Внешние инструменты...**, нажмите кнопку **Добавить**, а затем введите данные. Например, следующая запись вызывает открытие проводника Windows в каталоге с файлом, который в настоящий момент открыт в Visual Studio:  
  
1.  Заголовок: *Открыть расположение файла*
  
2.  Команда: `explorer.exe`  
  
3.  Аргументы: `/root, "$(ItemDir)"`  
  
 Ниже приведен полный список аргументов, которые можно использовать при определении внешнего инструмента.
  
> [!NOTE]
>  В строке состояния интегрированной среды разработки отображаются переменные "Текущая строка" и "Текущий столбец" для указания расположения точки вставки в активном редакторе кода. Переменная "Текущий текст" возвращает текст или код, выделенный в этом расположении.  
  
|Имя|Аргумент|Описание|  
|----------|--------------|-----------------|  
|Путь к элементу|$(ItemPath)|Полное имя файла текущего файла (диск + путь + имя файла).|  
|Каталог элемента|$(ItemDir)|Каталог текущего файла (диск + путь).|  
|Имя файла элемента|$(ItemFilename)|Имя файла текущего файла (имя файла).|  
|Расширение элемента|$(ItemExt)|Расширение имени файла текущего файла.|  
|Текущая строка|$(CurLine)|Строка текущего положения курсора в окне кода.|  
|Текущий столбец|$(CurCol)|Столбец текущего положения курсора в окне кода.|  
|Текущий текст|$(CurText)|Выбранный текст.|  
|Целевой путь|$(TargetPath)|Полное имя файла элемента для сборки (диск + путь + имя файла).|  
|Конечный каталог|$(TargetDir)|Каталог элемента для сборки.|  
|Целевое имя|$(TargetName)|Имя файла элемента для сборки.|  
|Конечное расширение|$(TargetExt)|Расширение имени файла элемента для сборки.|  
|Каталог двоичного файла|$(BinDir)|Конечное расположение двоичного файла, сборка которого выполняется (диск + путь). Например:**\\...\My Documents\Visual Studio \<Version>\\<имя_проекта\>\bin\debug**|  
|Каталог проекта|$(ProjDir)|Каталог текущего проекта (диск + путь).|  
|Имя файла проекта|$(ProjFileName)|Имя файла текущего проекта (диск + путь + имя файла).|  
|Каталог решения|$(SolutionDir)|Каталог текущего решения (диск + путь).|  
|Имя файла решения|$(SolutionFileName)|Имя файла текущего решения (диск + путь + имя файла).|  

## <a name="see-also"></a>См. также  
 [Средства сборки С/C++](/cpp/build/reference/c-cpp-build-tools)

