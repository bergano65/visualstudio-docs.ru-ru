---
title: Задача BscMake | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3ae418c8448fc2ebe4f5b2af0a8c713458988fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571690"
---
# <a name="bscmake-task"></a>Задача BscMake
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача BscMake](https://docs.microsoft.com/visualstudio/msbuild/bscmake-task).  
  
  
ВАЖНО]
>  BSCMAKE больше не используется в интегрированной среде разработки Visual Studio. Начиная с Visual Studio 2008, сведения о просмотре автоматически сохраняются в SDF-файле в папке решения.  
  
 Заключает в оболочку средство «Программа управления сведениями о просмотре Майкрософт» (bscmake.exe).  Средство bscmake.exe создает файл сведений о просмотре (BSC-файл) из исходных файлов браузера (SBR-файлов), созданных во время компиляции. Используйте **обозреватель объектов** для просмотра BSC-файла. Дополнительные сведения см. в разделе [Справочник по BSCMAKE](http://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описываются параметры задачи **BscMake**. Большинство параметров задач соответствуют параметрам командной строки.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|**AdditionalOptions**|Необязательный параметр типа **String**.<br /><br /> Список параметров, как указано в командной строке. Например, "/*параметр_1* /*параметр_2* /*параметр_#*". Этот параметр используется для указания параметров, не представленных каким-либо другим параметром задачи **BscMake**.<br /><br /> Дополнительные сведения см. в разделе [Параметры BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Необязательный параметр типа **String**.<br /><br /> Задает имя файла, которое переопределяет имя выходного файла по умолчанию.<br /><br /> Дополнительные сведения см. в описании параметра **/o** в разделе [Параметры BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, выполняется недобавочная сборка. Полная недобавочная сборка происходит независимо от того, существует ли BSC-файл, и предотвращает усечение SBR-файлов.<br /><br /> Дополнительные сведения см. в описании параметра **/n** в разделе [Параметры BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Sources**|Необязательный параметр **ITaskItem[]**.<br /><br /> Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.|  
|**SuppressStartupBanner**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/NOLOGO** в разделе [Параметры BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Необязательный параметр типа **String**.<br /><br /> Задает каталог для журнала отслеживания.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



